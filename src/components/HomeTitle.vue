<script setup lang="ts">
import { ref, watch } from 'vue';

const scrollPosition = ref(0);

watch(scrollPosition, (newValue) => {
  if (newValue > 0) {
    // Scroll position is not at the top
    console.log('Scroll position is not at the top');
    document.querySelector('#hovering')?.classList.remove('at-top');
  } else {
    // Scroll position is at the top
    console.log('Scroll position is at the top');
    document.querySelector('#hovering')?.classList.add('at-top');
  }
});

window.addEventListener('scroll', () => {
  scrollPosition.value = window.pageYOffset || document.documentElement.scrollTop;
});
</script>

<template>
    <div id="title">
      <div>
        <h1>Victor Santos</h1>
        <h1>Consulting</h1>
      </div>
      <div id="hovering" class="at-top">
        <h1>Victor Santos</h1>
        <h1>Consulting</h1>
      </div>
    </div>
</template>

<style scoped>
#title {
  position: relative;
  width: fit-content;
}

h1 {
  position: relative;
  font-size: 8vw;
  font-weight: bolder;
  line-height: 8vw;
  color: var(--color-heading);
  margin-left: 16px;
  width: fit-content;
}

div:first-child {
  position: absolute;
  color: var(--color-background-bis);
}

div:first-child > h1 {
  color: var(--color-background-bis);
}

div:last-child {
  transition: all 200ms ease-in-out;
}

.at-top {
  transform: translate(.8vw, -.8vw);
}
</style>