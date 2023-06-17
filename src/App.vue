<script setup lang="ts">
import { ref, provide } from 'vue';
import { RouterLink, RouterView } from 'vue-router';
import LangIcon from '@/components/icons/LangIcon.vue';

const unactiveLang = ref(window.navigator.language === 'fr-FR' ? 'eng' : 'fr');
const lang = ref(window.navigator.language !== 'fr-FR' ? 'eng' : 'fr');

const switchLang = () => {
  unactiveLang.value = lang.value; 
  lang.value = lang.value === 'fr' ? 'eng' : 'fr'; 
}

provide('lang', lang);
</script>

<template>
  <article>
    <header>
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
    </header>

    <section id="head">
      <div class="verticalflex">
        <main>
          <RouterView />
        </main>

        <nav>
          <div>
            <RouterLink to="/"><h1 class="link">VSC .</h1></RouterLink>
            <h1 class="link">VSC .</h1>
          </div>
          <div>
            <RouterLink to="/about"><h1 class="link">ABOUT</h1></RouterLink>
            <h1 class="link">ABOUT</h1>
          </div>
        </nav>
      </div>

      <footer>
        Made with Vue3
      </footer>
    </section>
  </article>
</template>

<style scoped>

footer {
  position: absolute;
  bottom: 0;
  right: 0;
  font-size: 10px;
  color: var(--color-heading);
}

header {
  position: fixed;
  right: 0%;
}

.langSwitch {
  display: flex;
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

main {
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: 8px;
  width: 80vw;
  transform: translateX(-100%);
  animation: intro 200ms ease-in-out 100ms forwards;
}

@keyframes intro {
  100%{
    transform: translateX(0);
  }
}

article {
  height: 100vh;
  overflow-y: scroll;
  /* scroll-snap-type: y mandatory; */
}

article section {
  /* scroll-snap-align: start; */
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

div.verticalflex {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

nav {
  position: fixed;
  right: 0px;
  height: 30vh;
  width: 20vw;
  display: flex;
  flex-direction: column;
  justify-content: center;
  transform: translateY(-100vh);
  animation: navanim 200ms ease-in 100ms forwards;
}

@keyframes navanim {
  100%{
    transform: translateY(6vh);
  }
}

nav > div > a {
  position: absolute;
  z-index: 1;
}

nav > div > a:hover:not(.router-link-active) {
  animation: linkhover 100ms ease-in forwards;
}

@keyframes linkhover {
  100% {
    transform: translate(.25vw, -.25vw);
    filter: drop-shadow(.25vw .25vw .25vw rgba(0, 0, 0, 0.5));
  }
}

h1.link {
  font-size: 2.5vw;
  color: var(--color-heading);
  font-weight: bolder;
  width: fit-content;
}

a:not(.router-link-active) > h1 {
  color: var(--color-text);
}

@media (max-width: 768px) {
  h1.link {
    font-size: 5vw;
  }

  @keyframes linkhover {
    100% {
      transform: translate(.5vw, -.5vw);
      filter: drop-shadow(.4=5vw .5vw .5vw rgba(0, 0, 0, 0.5));
    }
  }
}
</style>
