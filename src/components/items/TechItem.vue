<script setup lang="ts">
import FrontIcon from '@/components/icons/abouticons/FrontIcon.vue';
import BackIcon from '@/components/icons/abouticons/BackIcon.vue';
import CloudIcon from '@/components/icons/abouticons/CloudIcon.vue';
import ChevronIcon from '@/components/icons/ChevronIcon.vue';

const openDrawer = (e: Event) => {
  const clicked = e.currentTarget as HTMLElement;
  document.querySelectorAll(".wrap").forEach((element) => {if(element !== clicked) element.classList.remove("show")});

  if (clicked.classList.contains("show")) {
    clicked.classList.remove("show");
  } else {
    clicked.classList.add("show");
  }
}
</script>

<template>

  <div class="wrap" @click="openDrawer">

    <div class="over">
      <FrontIcon height="64px" width="64px"/>
      <span>
        <h1>Front-end</h1>
        <ChevronIcon width="32px" height="32px"/>
      </span>
    </div>

    <div class="under">
      <div class="content">
        <h2>technologies</h2>
        <p>JavaScript: Vue.JS</p>
        <p>HTML5</p>
        <p>CSS / SCSS</p>
      </div>
    </div>

  </div>

  <div class="wrap" @click="openDrawer">

    <div class="over">
      <BackIcon height="64px" width="64px"/>
      <span>
        <h1>Back-end</h1>
        <ChevronIcon width="32px" height="32px"/>
      </span>
    </div>

    <div class="under">
      <div class="content">
        <h2>technologies</h2>
        <p>PHP: Symfony</p>
        <p>JavaScript: Nest.JS</p>
        <p>C#: dotnet</p>
      </div>
    </div>

  </div>

  <div class="wrap" @click="openDrawer">

    <div class="over">
      <CloudIcon height="64px" width="64px"/>
      <span>
        <h1>Cloud / Server</h1>
        <ChevronIcon width="32px" height="32px"/>
      </span>
    </div>

    <div class="under">
      <div class="content">
        <h2>technologies</h2>
        <p>Cloud: Render, Hostinger, OVH, Azure</p>
        <p>Linux</p>
        <p>SQL</p>
      </div>
    </div>

  </div>

</template>

<style scoped> 
  div {
    width: 100%;
    height: 128px;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .wrap {
    -webkit-user-select: none;
    -ms-user-select: none;
    user-select: none;
    margin: 8px 0;
    background-color: var(--color-heading);
    transition: all 200ms ease-in-out;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 8px;
  }

  .over {
    border-radius: 8px;
    padding: 8px;
    background-color: var(--color-text);
    transition: all 200ms ease-in-out;
    z-index: 1;
  }

  span {
    display: flex;
    align-items: center;
  }

  h1 {
    font-weight: bolder;
    text-transform: uppercase;
    font-size: 4vw;
    color: var(--color-background);
    margin-right: 8px;
  }

  .under {
    position: absolute;
    width: 50vw;
    height: 128px;
    background-color: var(--color-background-bis);
    transition: all 200ms ease-in-out;
    display: flex;
    flex-direction: column;
    justify-content: end;

    border-radius: 0 0 8px 8px;
  }

  .content {
    height: 90%;
    color: var(--color-heading);
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    font-size: 1rem;
  }

  h2 {
    text-decoration: underline;
    text-transform: uppercase;
  }

  .show > .over {
    transform: translate(8px, -8px);
    filter: drop-shadow(8px 8px 8px rgba(0, 0, 0, 0.5));
  }

  svg {
    transition: all 200ms ease-in-out;
  }

  .show > .over > span > svg {
    rotate: 90deg;
  }

  .show ~ .wrap {
    transform: translateY(90%);
  }

  .show > .under {
    transform: translate(8px, 90%);
  }

  @media (max-width: 768px) {
    .content {
      font-size: .7rem;
    }
  }

  @media (max-width: 425px) {
    svg {
      height: 32px;
      width: 32px;
    }

    .content {
      height: 90%;
      color: var(--color-heading);
      display: flex;
      flex-direction: column;
      justify-content: flex-start;
      font-size: .7rem;
    }
  }
</style>