<script setup lang="ts">
import IconLang from '@/components/icons/IconLang.vue';
import HomeView from '@/views/HomeView.vue';
import AboutView from '@/views/AboutView.vue';
import ProjectView from '@/views/ProjectView.vue';
import { onMounted, provide, ref, watch } from 'vue';
import * as anim from '@/utils.anim';

// scroll indicator handling and paralax

const scrollIndicatorWidth = ref(0);
const scrollIndicatorStyle = ref('');
const decoStyle = ref('');

const handleScroll = () => {
  const scrollTop = window.pageYOffset || document.documentElement.scrollTop;
  const scrollHeight =
    document.documentElement.scrollHeight -
    document.documentElement.clientHeight;
  const progress = (scrollTop / scrollHeight) * 100;
  scrollIndicatorWidth.value = progress;
};

window.addEventListener('scroll', handleScroll);

watch(scrollIndicatorWidth, () => {  
  anim.translate('#deco', `${scrollIndicatorWidth.value * .5}%`, `${scrollIndicatorWidth.value * .5}%`, 0);

  scrollIndicatorStyle.value = `width: ${scrollIndicatorWidth.value}%`;
});

// language switching handling

const unactiveLang = ref(window.navigator.language === 'fr-FR' ? 'eng' : 'fr');
const lang = ref(window.navigator.language !== 'fr-FR' ? 'eng' : 'fr');

const switchLang = () => {
  unactiveLang.value = lang.value; 
  lang.value = lang.value === 'fr' ? 'eng' : 'fr'; 
}

provide('lang', lang);

// section switching handling

const navItems = [
  { label: 'VSC .', to: '#home' },
  { label: 'ABOUT', to: '#about' },
  { label: 'CODE', to: '#project' }
];

let lastActive: string = '';

const isElementAbove = (element1: HTMLElement, element2: HTMLElement) => element1.offsetTop < element2.offsetTop;

const handleSectionIntersection = (entries: IntersectionObserverEntry[]) => {
  entries.forEach(entry => {
    const sectionId = entry.target.id;
    const navItem = navItems.find(item => item.to === `#${sectionId}`);

    if (navItem) {      
      if (entry.isIntersecting) {

        const intersectingElement = document.querySelector(navItem.to) as HTMLElement;

        if (lastActive !== navItem.to) {
          if (lastActive !== '') {
            const lastElement = document.querySelector(lastActive) as HTMLElement;
            
            anim.translateY(`${lastActive}-title`, isElementAbove(intersectingElement, lastElement) ? '48px' : '-48px');
            anim.hide(`${lastActive}-title`, true);
          }

          anim.hide(`${navItem.to}-title`, false);
          anim.translateY(`${navItem.to}-title`, '0px');

          lastActive = navItem.to;
        }
      }
    }
  });
};

onMounted(() => {
  const sections = document.querySelectorAll("section");
  const options = {
    root: null, // Use the viewport as the root
    rootMargin: "0px",
    threshold: .7 // When at least 50% of the section is visible
  };

  const observer = new IntersectionObserver(handleSectionIntersection, options);

  sections.forEach(section => observer.observe(section));
});
</script>

<template>

  <div id="lang-switch" @click="switchLang">
    <IconLang/>
    <span>
      <h3>{{ lang === 'fr' ? 'eng' : 'fr' }}</h3>
      <h3>{{ lang === 'fr' ? 'fr' : 'eng' }}</h3>
    </span>
  </div>

  <header>
    <h1 id="home-title">vsc .</h1>
    <h1 id="about-title">{{ lang === 'fr' ? 'a propos' : 'about' }}</h1>
    <h1 id="project-title">{{ lang === 'fr' ? 'projets' : 'projects' }}</h1>
  </header>

  <div id="deco" :style="decoStyle"></div>

  <section id="home">
    <HomeView/>
  </section>

  <section id="about">
    <AboutView/>
  </section>

  <section id="project">
    <ProjectView/>
  </section>

  <div class="scroll-indicator" :style="scrollIndicatorStyle"></div>
</template>

<style scoped>
#lang-switch {
  position: fixed;
  top: 0;
  left: 0;
  z-index: 3;
  display: flex;
  cursor: pointer;
}

#lang-switch > span > h3 {
  line-height: 24px;
  font-weight: bolder;
  color: var(--color-background);
}

#lang-switch > span > h3:first-child {
  color: var(--color-background-bis);
}

header {
  position: fixed;
  top: 0;
  width: 100%;
  height: 48px;
  background-color: var(--color-heading);
  display: flex;
  justify-content: end;
  z-index: 2;
}

header > h1 {
  position: absolute;
  font-weight: bolder;
  font-size: 48px;
  line-height: 48px;
  text-transform: uppercase;
  color: var(--color-background);
  transform: translateY(48px);
  user-select: none;
  opacity: 0;
}

.scroll-indicator {
  position: fixed;
  top: 48px;
  left: 0;
  height: 4px;
  width: 0;
  background-color: var(--color-background-bis);
  z-index: 0;
}

section {
  position: relative;
  top: 48px;
  height: calc(100vh - 48px);
  z-index: 1;
}

#deco {
  position: fixed;
  background-color: var(--color-background-bis);
  /* transform: translate(50vw, 100vh); */
  width: 70vw;
  height: 100vh;
  rotate: 45deg;
  top: 0;
  left: 50vw;
}

</style>
