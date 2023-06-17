<script setup lang="ts">import { inject, ref, toRef, watch } from 'vue';

const eng = "Looking for a skilled problem-solving developer? With recognized expertise in decoding technical challenges, I turn complexities into elegant and efficient solutions. My ability to navigate through code and find optimized solutions will provide you with undeniable value. My talent for quickly understanding needs and adapting my skills allows me to deliver tailor-made solutions. No matter the technological challenge, I am ready to take it on.";
const fr = "Recherchez-vous un développeur habile en résolution de problèmes ? Avec une expertise reconnue dans le décodage des défis techniques, je transforme les complexités en solutions élégantes et efficaces. Ma capacité à naviguer dans le code et à trouver des solutions optimisées vous fournira une valeur indéniable. Mon talent pour comprendre rapidement les besoins et adapter mes compétences me permet d'offrir des solutions sur mesure. Peu importe le défi technologique, je suis prêt à le relever.";

const lang = toRef(inject('lang'));
const text = ref(lang.value === 'fr' ? fr : eng);

watch(() => lang.value, () => {
  text.value = lang.value === 'fr' ? fr : eng;
});
</script>

<template>
  <main>
    <div class="about">
      <p>
        {{ text }}
      </p>
    </div>
  </main>
</template>

<style scoped>
.about {
  width: 100%;
  padding: 16px;
}

p {
  text-align: justify;
  color: var(--color-heading);
  font-size: 2vw;
}

@media (max-width: 768px) {
  p {
    font-size: 4vw;
  }
}
</style>
