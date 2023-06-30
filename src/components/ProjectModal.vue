<script setup lang="ts">
import IconChevron from '@/components/icons/IconChevron.vue';
import IconLink from './icons/IconLink.vue';
import { inject, ref } from 'vue';

const lang = ref(inject('lang'));

const props = defineProps<{
  title: string,
  date: string,
  job: {fr: string, eng: string},
  tasks: {fr: string[], eng: string[]},
  links: {label: string, link: string}[],
}>()

const emit = defineEmits<{
  (e: 'closeModal'): void
}>()

const closeModalEmit = () => emit('closeModal');
</script>

<template>
  <div id="project-modal">
    <div id="modal-header">
      <h2>{{ date }}</h2>
      <h1>{{ props.title }}</h1>
      <IconChevron @click="closeModalEmit"/>
    </div>
    <h1>{{ lang === 'fr' ? job.fr : job.eng }}</h1>
    <div id="modal-content">
      <ul>
        <li v-for="task in (lang === 'fr' ? tasks.fr : tasks.eng)" :key="task">{{ task }}</li>
      </ul>
      <ul id="modal-links">
        <li id="link" v-for="link in links" :key="link.label">
          <a :href="link.link" target="_blank">
            <h2>{{ link.label }}</h2>
            <IconLink/>
          </a>
        </li>
      </ul>
    </div>
  </div>
</template>

<style scoped>
#project-modal {
  position: fixed;
  height: 50vh;
  width: 100vw;
  top: 100%;
  left: 0;
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
  justify-content: space-between;
  align-items: center;
}

#modal-header > h1 {
  text-align: center;
  color: var(--color-background-bis);
  font-weight: bolder;
  font-size: 32px;
}

#modal-header > h2 {
  text-align: center;
  color: var(--color-background-bis);
  font-weight: bolder;
  font-size: 16px;
  white-space: pre;
  margin-left: 4px;
}

#project-modal > h1 {
  color: var(--color-background-bis);
  font-weight: bolder;
  font-size: 24px;
}

#modal-content {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: space-between;
}

ul {
  color: var(--color-background-bis);
  font-size: 16px;
  width: 60%;
}

#modal-links{
  list-style-type: none;
  display: flex;
  flex-direction: column;
  align-items: end;
  width: fit-content;
}

#link {
  background-color: var(--color-background);
  border-radius: 8px 0 0 8px;
  margin: 8px 0;
  height: 32px;
  width: 128px;
}

a {
  color: var(--color-heading);
  display: flex;
  width: 100%;
  align-items: center;
  justify-content: end;
  text-decoration: underline;
  height: 32px;
  padding-right: 8px;
  border-radius: 8px 0 0 8px;
}

a > h2 {
  font-size: 16px;
}

a:hover {
  background-color: var(--color-hover);
}
</style>