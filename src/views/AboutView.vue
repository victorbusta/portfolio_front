<script setup lang="ts">
import { inject, onMounted, ref, watch } from 'vue';

const lang = ref(inject('lang'));

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

      <div id="skill-card">
        <div id="card-content">
          <h1>Front-end</h1>
        </div>
        <div id="card-img" >
          <img src="../../public/front_end.jpg" alt="">
        </div>
      </div>

      <div id="skill-card">
        <div id="card-content">
          <h1>Back-end</h1>
        </div>
        <div id="card-img" >
          <img src="../../public/back_end.jpg" alt="">
        </div>
      </div>

      <div id="skill-card">
        <div id="card-content">
          <h1>Cloud</h1>
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
  background-color: black;
  transform: translateX(-50%);
  /* scale: 10; */
}

img {
  position: relative;
  width: 150%;
  object-fit: cover;
}

#card-content {
  position: absolute;
  color: white;
  width: 100%;
  z-index: 1;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
}

#skill-card:first-child {
  border-radius: 8px 0 0 8px;
}

#skill-card:last-child {
  border-radius: 0 8px 8px 0;
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
}
</style>
