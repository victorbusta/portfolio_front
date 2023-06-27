<script setup lang="ts">
import HomeTitle from '@/components/HomeTitle.vue';
import IconGithub from '@/components/icons/IconGithub.vue';
import IconLinked from '@/components/icons/IconLinked.vue';
import IconMalt from '@/components/icons/IconMalt.vue';
import IconMail from '@/components/icons/IconMail.vue';
import IconResume from '@/components/icons/IconResume.vue';
</script>

<template>
  <main>
    <div>
      <HomeTitle/>
      <span>
        <IconGithub/>
        <IconLinked/>
        <IconMalt/>
        <IconMail/>
        <IconResume/>
      </span>
    </div>
  </main>
</template>

<style scoped>
main {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

div {
  display: flex;
  flex-direction: column;
  justify-content: center;
  width: fit-content;
}

span {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 16px;
}

span > a {
  margin: 0 8px;
}
</style>
