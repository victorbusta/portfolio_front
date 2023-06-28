<script setup lang="ts">
import IconEye from '@/components/icons/IconEye.vue';
import Modal from '@/components/ProjectModal.vue';
import { delay } from '@/utils.anim';
import { onMounted, ref } from 'vue';

const modalTitle = ref('');

const openModal = async () => {
  document.querySelector('#project-modal')?.classList.remove('active-modal');
  await delay(200);
  document.querySelector('#project-modal')?.classList.add('active-modal');
}

</script>

<template>
  <main>
    <div id="caroussel">

      <div id="caroussel-item" @click="openModal">
        <IconEye/>
        <div id="item-img">
          <img src="../../public/vanbutsele_web.png" alt="">
        </div>
        <div id="item-content">
          <div id="item-title">
            <h2>04/2023<br>06/2023</h2>
            <h1>VanButsele</h1>
          </div>
        </div>
      </div>

      <div id="caroussel-item" @click="openModal">
        <IconEye/>
        <div id="item-img">
          <img src="../../public/muzikaloid_web.png" alt="">
        </div>
        <div id="item-content">
          <div id="item-title">
            <h2>02/2023<br>06/2023</h2>
            <h1>Muzikaloid</h1>
          </div>
        </div>
      </div>

      <div id="caroussel-item" @click="openModal">
        <IconEye/>
        <div id="item-img">
          <img src="../../public/visiteonline.png" alt="">
        </div>
        <div id="item-content">
          <div id="item-title">
            <h2>05/2021<br>12/2022</h2>
            <h1>VisiteOnline</h1>
          </div>
        </div>
      </div>

    </div>

    <Modal/>
  </main>
</template>

<style scoped>
main {
  width: 100%;
  min-height: 100%;
}

#caroussel {
  width: 100%;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

#caroussel-item {
  position: relative;
  width: 25vw;
  height: 30vh;
  background-color: black;
  margin:  32px 16px 16px 16px;
  border-radius: 8px;
}

#caroussel-item > svg {
  position: absolute;
  z-index: 2;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

#item-img {
  position: absolute;
  height: 100%;
  width: 100%;
  overflow: hidden;
  border-radius: 8px 8px 0 0;
  display: flex;
  justify-content: center;
  align-items: start;
}

img {
  width: 150%;
  border-radius: 8px;
}

#item-content {
  position: relative;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.6);
  z-index: 1;
  border-radius: 8px 8px 0 0;
  display: flex;
  align-items: end;
}

#item-title {
  position: relative;
  height: 20%;
  width: 100%;
  background-color: var(--vt-c-black-bis);
  border-radius: 0 0 8px 8px;
  transform: translateY(100%);
  padding: 0 8px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

#item-title > h1 {
  font-weight: bolder;
  color: var(--vt-c-white);
}

#item-title > h2 {
  font-size: 2vh;
  color: var(--vt-c-white-bis);
}

@media (max-width: 768px) {
  #item-img {
    border-radius: 8px;
  }

  #item-content {
    border-radius: 8px;
  }

  #item-title {
    height: 20%;
    width: 100%;
    border-radius: 0 0 8px 8px;
    transform: translateY(0%);
  }

  #caroussel > div {
    width: 60vw;
    height: 30vh;
  }

  /* img {
    height: 100%;
    width: auto;
  } */
}

@media (max-width: 425px) {

  #item-title {
    height: 25%;
  }

  #item-title > h2 {
  }

  #caroussel > div {
    width: 80vw;
    height: 25vh;
    background-color: black;
  }
}
</style>
