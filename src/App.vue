<script setup lang="ts">
import { ref, provide, onMounted } from 'vue';
import LangIcon from '@/components/icons/LangIcon.vue';
import NavItem from './components/items/NavItem.vue';
import HomeView from './views/HomeView.vue';
import AboutView from './views/AboutView.vue';
import CodeView from './views/CodeView.vue';

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
      navItem.isActive.value = entry.isIntersecting;
      if (entry.isIntersecting) {
        window.location.hash = navItem.to;  // updates the URL hash when isActive is true
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

</script>

<template>

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
      Made with Vue3
  </footer>

</template>

<style scoped>
article {
  overflow-y: scroll;
  -ms-overflow-style: none;
  scrollbar-width: none;
  min-height: 100vh;
  width: 100%;
  display: grid;
  grid-template-columns: 100%;
  grid-row: auto;
  transform: translateX(-100%);
  animation: intro 200ms ease-in-out 100ms forwards;
  scroll-behavior: smooth;
}

article::-webkit-scrollbar {
  display: none;
}

section {
  grid-column-start: 1;
  scroll-snap-align: start;
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
  right: 8px;
  font-size: 10px;
  color: var(--color-heading);
  z-index: 1;
}

.langSwitch {
  position: fixed;
  right: 0%;
  display: flex;
  z-index: 2;
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
  transform: translateX(100%);
  animation: navanim 200ms ease-in 100ms forwards;
  z-index: 1;
  /* background: linear-gradient(270deg, var(--color-background) 50%, rgba(255, 255, 255, 0) 100%); */
}

@keyframes navanim {
  100%{
    transform: translateX(0);
  }
}

@media (max-width: 768px) {
  /* @keyframes navanim {
    100%{
      transform: translateY(75vh);
    }
  } */
}
</style>
