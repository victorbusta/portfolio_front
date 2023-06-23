<script setup lang="ts">
import { inject, ref } from 'vue';
import TechItem from '@/components/items/TechItem.vue';

const lang = ref(inject('lang'));
</script>

<template>
  <main>
    <p v-if="lang === 'fr'">
    Salut !<br>
    Je suis <span>Victor Santos</span>, un développeur français passionné résident à Paris.<br>
    En quête de perfection, je cherche toujours à améliorer et partager mes compétences.
  </p>
  <p v-else>
    Hello there !<br>
    I am <span>Victor Santos</span>, a passionate french developer based in Paris.<br>
    Striving for perfection, I'm always looking for ways to improve and share my knowledge.
  </p>

  <TechItem/>
  </main>

</template>

<style scoped>
main {
  margin: 0 10vw;
  height: fit-content;
  padding: 16px;
  display: flex;
  flex-direction: column;
}

div {
  display: flex;
  flex-direction: column;
  align-items: center;
}

p {
  /* text-align: justify; */
  color: var(--color-heading);
  font-size: 1.5rem;
  font-weight: bolder;
  /* white-space: pre-wrap; */
}

p > span {
  font-weight: bolder;
  color: var(--color-text);
}

@media (max-width: 768px) {
  main {
    margin: 0;
  }

  p {
    font-size: 1rem;
  }
}
</style>
