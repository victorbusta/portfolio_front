<script setup lang="ts">
const navdata = defineProps({
  label: {
    type: String,
    required: true
  },
  to: {
    type: String,
    required: true
  },
});

</script>

<template>
  <a :href="navdata.to">
    <h1>{{ navdata.label }}</h1>
    <h1>{{ navdata.label }}</h1>
  </a>
</template>

<style scoped>
a {
  position: relative;
}

h1 {
  font-size: 4vw;
  font-weight: bolder;
  color: var(--color-heading);
}

h1:first-child {
  position: absolute;
  color: var(--color-text);
  transition: all 200ms ease-in-out;
}

a:hover > h1:first-child {
  transform: translate(.4vw, -.4vw);
  filter: drop-shadow(.4vw .4vw .4vw rgba(0, 0, 0, 0.5));
}

.active > h1:first-child {
  transform: translate(.4vw, -.4vw);
  filter: drop-shadow(.4vw .4vw .4vw rgba(0, 0, 0, 0.5));
}
</style>