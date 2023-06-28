<script setup lang="ts">
import IconChevron from '@/components/icons/IconChevron.vue';
import { ref } from 'vue';

const props = defineProps({
  title: ref,
})

const closeModal = () => document.querySelector('#project-modal')?.classList.remove('active-modal');
</script>

<template>
  <div id="project-modal">
    <div id="modal-header">
      <IconChevron @click="closeModal"/>
    </div>
  </div>
</template>

<style scoped>
#project-modal {
  position: fixed;
  height: 50vh;
  width: 100vw;
  top: 100%;
  background-color: var(--color-heading);
  z-index: 2;
  display: flex;
  flex-direction: column;
  transition: transform 200ms ease-in-out;
}

.active-modal {
  transform: translateY(-100%);
}

#modal-header {
  width: 100%;
  height: 48px;
  border-bottom: solid 1px var(--color-background-bis);
  display: flex;
  justify-content: end;
}
</style>