<script setup lang="ts">
import Logo from '@/components/LogoIcon.vue';
import GithubIcon from '@/components/icons/GithubIcon.vue';
import LinkedIcon from '@/components/icons/LinkedIcon.vue';
import MailIcon from '@/components/icons/MailIcon.vue';
import ResumeIcon from '@/components/icons/ResumeIcon.vue';
import { inject, watch, toRef, ref } from 'vue';

const eng = "Fullstack developper";
const fr = 'Développeur full-stack';


const lang = toRef(inject('lang'));
const title = ref(lang.value === 'fr' ? fr : eng);

watch(() => lang.value, () => {
  title.value = lang.value === 'fr' ? fr : eng;
});
</script>

<template>
  <main>
    <Logo id="logo"/>
    <h1>{{ title }}</h1>
    <div>
      <a class="iconlink" href="https://github.com/victorbusta" target="_blank"><GithubIcon/></a>
      <a class="iconlink" href="https://www.linkedin.com/in/victor-busta/" target="_blank"><LinkedIcon/></a>
      <a class="iconlink" href="mailto:victor.sdbustamante@gmail.com?subject=Prise de contact" target="_blank"><MailIcon/></a>
      <a class="iconlink" href="./cv-VictorSantos.pdf" target="_blank"><ResumeIcon/></a>
    </div>
</main>
</template>

<style scoped>
#logo {
  width: 100%;
}

main {
  display: flex;
  flex-direction: column;
}

h1 {
  width: 100%;
  font-size: 3vw;
  font-weight: bolder;
  color: var(--color-heading);
}

div {
  width: 100%;
  display: flex;
  justify-content: center;
}

.iconlink {
  height: 32px;
  width: 32px;
  margin: 0 8px;
}

@media (max-width: 768px) {
  h1 {
    font-size: 4.5vw;
  }
}
</style>