<script setup lang="ts">
import { inject, onMounted, ref, watch } from 'vue';

const lang = ref(inject('lang'));

const displayCard = (e: Event) => {
  const element = e.currentTarget as HTMLElement;
  const title = element.querySelector('#card-title');
  const list = element.querySelector('#content-list');  

  if (!title?.classList.contains('hidden')) {
    title?.classList.add('hidden');
    list?.classList.remove('hidden');
  } else {
    title?.classList.remove('hidden');
    list?.classList.add('hidden');
  }

}

</script>

<template>
  <main>
    <p v-if="lang === 'fr'">
      Bonjour !<br>
      Je m'appelle <span>Victor Santos</span>, un développeur passionné résidant à Paris.<br>
      En quête de perfection, je cherche toujours à améliorer et partager mes compétences.
    </p>
    <p v-else>
      Hello there !<br>
      I am <span>Victor Santos</span>, a passionate developer based in Paris.<br>
      Striving for perfection, I'm always looking for ways to improve and share my knowledge.
    </p>
    <div id="skills">

      <div id="skill-card" @click="displayCard">
        <div id="card-content">
          <div id="card-title">
            <h1>Front-end</h1>
          </div>

          <div id="content-list" class="hidden">
            <h2>JS / Vue.JS</h2>
            <h2>HTML5</h2>
            <h2>CSS / SCSS</h2>
          </div>
        </div>
        <div id="card-img" >
          <img src="../../public/front_end.jpg" alt="">
        </div>
      </div>

      <div id="skill-card" @click="displayCard">
        <div id="card-content">
          <div id="card-title">
            <h1>Back-end</h1>
          </div>

          <div id="content-list" class="hidden">
            <h2>PHP / Symfony</h2>
            <h2>JS / Nest.JS</h2>
            <h2>C# / .Net</h2>
          </div>
        </div>
        <div id="card-img" >
          <img src="../../public/back_end.jpg" alt="">
        </div>
      </div>

      <div id="skill-card" @click="displayCard">
        <div id="card-content">
          <div id="card-title">
            <h1>Cloud</h1>
          </div>

          <div id="content-list" class="hidden">
            <h2>OVH / Azure</h2>
            <h2>Linux</h2>
            <h2>SQL</h2>
          </div>
        </div>
        <div id="card-img" >
          <img src="../../public/cloud.jpg" alt="">
        </div>
      </div>

    </div>
  </main>
</template>

<style scoped>
main {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
}

#title > h1 {
  font-size: 8vw;
  font-weight: bolder;
  /* line-height: 8vw; */
  color: var(--color-heading);
  margin-left: 16px;
  width: fit-content;
}

p {
  color: var(--color-heading);
  font-size: 1.2rem;
  font-weight: bolder;
  width: 80%;
  margin-left: 16px;
  text-align: start;
}

p > span {
  font-weight: bolder;
  color: var(--color-text);
}

#skills {
  width: 100%;
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  margin-top: 32px;
}

#skill-card {
  position: relative;
  height: 50vh;
  width: 20vw;
  margin: 0 2px;
  overflow: hidden;
}

#skill-card > #card-img{
  width: 200%;
  height: 100%;
  transform: translateX(-50%);
  transition: all 200ms ease-in-out;
}

img {
  position: relative;
  width: 150%;
  object-fit: cover;
}

#card-content {
  position: absolute;
  color: var(--vt-c-white);
  width: 100%;
  z-index: 1;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.7);
  padding: 4px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  user-select: none;
}

#card-content:hover ~ #card-img {
  scale: 1.1;
}

#skill-card:first-child {
  border-radius: 8px 0 0 8px;
}

#skill-card:last-child {
  border-radius: 0 8px 8px 0;
}

#card-title {
  position: absolute;
  transition: all 200ms ease-in-out;
  text-transform: uppercase;
}

#content-list {
  transition: all 200ms ease-in-out;
}

.hidden {
  opacity: 0;
}

@media (max-width: 768px) {

  img {
    object-fit: cover;
    transform: translateY(-50%);
  }

  #skill-card {
    height: 20vh;
    width: 70vw;
    margin: 2px 0;
  }
  
  #skill-card:first-child {
    border-radius: 8px 8px 0 0;
  }

  #skill-card:last-child {
    border-radius: 0 0 8px 8px;
  }
}

@media (max-width: 425px) {
  p {
    font-size: .8rem;
  }

  #skill-card {
    height: 15vh;
    width: 70vw;
  }

  #content-list {
    font-size: .7rem;
  }
}
</style>
