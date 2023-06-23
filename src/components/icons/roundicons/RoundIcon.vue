<script setup lang="ts">
const icon = defineProps({
  svg: {
    type: String,
    required: true,
  }
});

const getParsedSvgIcon = () => {
  const parser = new DOMParser();
  const doc = parser.parseFromString(icon.svg, 'image/svg+xml');
  return doc.documentElement.outerHTML;
};

const iconElement = getParsedSvgIcon();
</script>

<template>
  <div>
    <div v-html="iconElement"></div>
    <!-- {{ iconElement }}
    {{ iconElement }} -->
  </div>
</template>

<style scoped>
svg {
  width: 32px;
  height: 32px;
}
.back {
  /* fill: var(--color-background); */
  fill: none;
}

#under {
  fill: var(--color-heading);
  position: absolute;
}

#over {
  fill: var(--color-text);
  z-index: 1;
  transition: all 200ms ease-in-out;
}

#over:hover {
  transform: translate(4px, -4px);
    filter: drop-shadow(4px 4px 4px rgba(0, 0, 0, 0.2));
}
</style>
