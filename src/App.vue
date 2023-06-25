<script setup lang="ts">
import { ref, provide, onMounted, watch } from 'vue';
import LangIcon from '@/components/icons/LangIcon.vue';
import NavItem from './components/items/NavItem.vue';
import HomeView from './views/HomeView.vue';
import AboutView from './views/AboutView.vue';
import CodeView from './views/CodeView.vue';
import * as anim from '@/utils.animation';

const scrollIndicatorWidth = ref(0);
const scrollIndicatorStyle = ref('');

const handleScroll = () => {
  const scrollTop = window.pageYOffset || document.documentElement.scrollTop;
  const scrollHeight =
    document.documentElement.scrollHeight -
    document.documentElement.clientHeight;
  const progress = (scrollTop / scrollHeight) * 100;
  scrollIndicatorWidth.value = progress;
};

onMounted(() => {
  window.addEventListener('scroll', handleScroll);
});

watch(scrollIndicatorWidth, () => {
  scrollIndicatorStyle.value = `width: ${scrollIndicatorWidth.value}%`;
});

const unactiveLang = ref(window.navigator.language === 'fr-FR' ? 'eng' : 'fr');
const lang = ref(window.navigator.language !== 'fr-FR' ? 'eng' : 'fr');

const switchLang = () => {
  unactiveLang.value = lang.value; 
  lang.value = lang.value === 'fr' ? 'eng' : 'fr'; 
}

provide('lang', lang);

const navItems = [
  { label: 'VSC .', to: '#home', isActive: ref(false) },
  { label: 'ABOUT', to: '#about', isActive: ref(false) },
  { label: 'CODE', to: '#project', isActive: ref(false) }
];

const handleSectionIntersection = (entries: IntersectionObserverEntry[]) => {
  entries.forEach(entry => {
    const sectionId = entry.target.id;
    const navItem = navItems.find(item => item.to === `#${sectionId}`);

    if (navItem) {
      if (entry.isIntersecting) {
        navItem.isActive.value = true;
        // window.history.replaceState({}, '', navItem.to); // Update URL hash without scrolling
      } else {
        navItem.isActive.value = false;
      }
    }
  });
};

onMounted(() => {
  const sections = document.querySelectorAll("section");
  const options = {
    root: null, // Use the viewport as the root
    rootMargin: "0px",
    threshold: 0.5 // When at least 50% of the section is visible
  };

  const observer = new IntersectionObserver(handleSectionIntersection, options);

  sections.forEach(section => observer.observe(section));
});

let navOpen = false;

const toggleNav = () => {
  if (window.innerWidth <= 425) {
    anim.translateX('nav', navOpen ? '100%' : '0', 100);
    navOpen = !navOpen;
    if (!navOpen) {
      document.querySelector('#burger')?.classList.remove("opened");
    } else {
      document.querySelector('#burger')?.classList.add("opened");
    }
  }
}

</script>

<template>

  <div class="scroll-indicator" :style="scrollIndicatorStyle"></div>

  <div class="langSwitch" @click="switchLang">
    <span>
      <h1 >
        {{ lang }}
      </h1>
      <h1 class="unactive">
        {{ unactiveLang }}
      </h1>
    </span>

    <LangIcon height="56px"/>
  </div>

  <nav>
    <NavItem
        v-for="navItem in navItems"
        :key="navItem.to"
        :label="navItem.label"
        :to="navItem.to"
        :class="`${navItem.isActive.value ? 'active' : ''}`"
        @click="toggleNav"
      />
  </nav>

  <article>
    <section id="home">
      <HomeView/>
    </section>
    <section id="about">
      <AboutView/>
    </section>
    <section id="project">
      <CodeView/>
    </section>
  </article>

  <footer>
    <div id="burger" @click="toggleNav">
      <div></div>
      <div></div>
      <div></div>
    </div>
      Made with Vue3
  </footer>

</template>

<style scoped>
.scroll-indicator {
  position: fixed;
  top: 0;
  left: 0;
  height: 4px;
  width: 0;
  background-color: var(--color-background-bis); /* Choose the desired background color */
  z-index: 2;
  transform-origin: left;
}

article {
  -ms-overflow-style: none;
  scrollbar-width: none;
  min-height: 100vh;
  width: 100%;
  display: flex;
  flex-direction: column;
  transform: translateX(-100%);
  animation: intro 200ms ease-in-out 100ms forwards;
  scroll-behavior: smooth;
}

article::-webkit-scrollbar {
  display: none;
}

section {
  grid-column-start: 1;
  width: 75vw;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  height: fit-content;
}

footer {
  position: fixed;
  bottom: 0;
  right: 0;
  padding-right: 8px;
  font-size: 10px;
  color: var(--color-heading);
  z-index: 1;
  display: flex;
  flex-direction: column;
  align-items: end;
}

.langSwitch {
  position: fixed;
  right: 0%;
  display: flex;
  z-index: 2;
}

.langSwitch > span {
  height: 64px;
}

.langSwitch > span > h1{
  color: var(--color-heading);
  font-size: 24px;
}

.langSwitch > span > h1:nth-child(n + 2){
  color: var(--color-text);
  transform: translateY(-16px);
  font-size: 24px;
}

@keyframes intro {
  100%{
    transform: translateX(0);
  }
}

nav {
  position: fixed;
  right: 0px;
  top: 0px;
  height: 100vh;
  width: 20vw;
  display: flex;
  flex-direction: column;
  justify-content: center;
  z-index: 1;
}

@keyframes navanim {
  100%{
    transform: translateX(0);
  }
}

@media (max-width: 425px) {

  .langSwitch {
    background-color: var(--color-background-bis-soft);
    padding-left: 8px;
    border-radius: 0 0 0 8px;

  }

  section {
    width: 100vw;
  }

  nav {
    transform: translateX(100%);
    background-color: var(--color-background-bis);
    width: 50vw;
    align-items: center;
    
  }

  #project {
    margin-bottom: 32px;
  }

  #burger {
    height: 48px;
    width: 48px;
    background-color: var(--color-background-bis-soft);
    padding: 4px;
    margin-bottom: 8px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    border-radius: 8px;
  }

  #burger > div {
    position: absolute;
    height: 4px;
    width: 40px;
    background-color: var(--color-text);
    border-radius: 4px;
    transition: all 200ms ease-in-out;
  }

  #burger:not(.opened) > div:first-child {
    transform: translateY(12px);
  }

  #burger:not(.opened) > div:last-child {
    transform: translateY(-12px);
  }

  .opened > div:first-child {
    transform: rotate(45deg);
  }

  .opened > div:last-child {
    transform: rotate(-45deg);
  }

  .opened > div:nth-child(2) {
    opacity: 0;
  }
}
</style>
