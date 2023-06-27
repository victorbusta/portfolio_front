<script setup lang="ts">
import { inject, ref } from 'vue';

const lang = ref(inject('lang'));
</script>

<template>
  <main>
    <p v-if="lang === 'fr'">
      Bonjour !<br>
      Je m'appelle <span>Victor Santos</span>, un développeur français passionné résidant à Paris.<br>
      En quête de perfection, je cherche toujours à améliorer et partager mes compétences.
    </p>
    <p v-else>
      Hello there !<br>
      I am <span>Victor Santos</span>, a passionate french developer based in Paris.<br>
      Striving for perfection, I'm always looking for ways to improve and share my knowledge.
    </p>

  </main>
</template>

<style scoped>
main {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  /* justify-content: center; */
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
  /* text-align: justify; */
  color: var(--color-heading);
  font-size: 1.2rem;
  font-weight: bolder;
  width: 80%;
  margin-left: 16px;
  text-align: start;
  /* white-space: pre-wrap; */
}

p > span {
  font-weight: bolder;
  color: var(--color-text);
}

@media (max-width: 425px) {
  p {
    font-size: .8rem;
  }
}
</style>
