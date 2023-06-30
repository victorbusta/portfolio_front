<script setup lang="ts">
import IconEye from '@/components/icons/IconEye.vue';
import Modal from '@/components/ProjectModal.vue';
import { delay } from '@/utils.anim';

let carousselItem: HTMLElement | null = null;

const openModal = async (e: Event) => {
  const element = e.currentTarget as HTMLElement;

  if (carousselItem !== null) {
    carousselItem.parentElement?.parentElement?.querySelector('#project-modal')?.classList.remove('active-modal');
    carousselItem.parentElement?.classList.remove('active-item');
    await delay(200);
  }

  if (carousselItem !== element) {
    element.parentElement?.parentElement?.querySelector('#project-modal')?.classList.add('active-modal');
    element.parentElement?.classList.add('active-item');
    carousselItem = element;
  } else {
    carousselItem = null;
  }
}

const closeModal = () => {  
  carousselItem?.parentElement?.parentElement?.querySelector('#project-modal')?.classList.remove('active-modal');
  carousselItem?.parentElement?.classList.remove('active-item');
  carousselItem = null;
}
</script>

<template>
  <main>
    <div id="caroussel">

      <div id="caroussel-item">
        <div id="item-wrapper">
          <div id="item-img">
            <img src="/vanbutsele_web.png" alt="">
          </div>
          <div id="item-content" @click="openModal">
            <IconEye/>
            <div id="item-title">
              <h2>04/2023<br>06/2023</h2>
              <h1>VanButsele</h1>
            </div>
          </div>
        </div>

        <Modal
          @closeModal="closeModal" 
          title="VanButsele" 
          date="04/23 - 06/23"
          :job="{
            fr: 'Développeur fullstack',
            eng: 'Fullstack developer'
          }"
          :tasks="{
            fr: [
              'Création d’un site de vente de photos',
              'Conception et réalisation du front-end',
              'Conception et réalisation d\'une API REST avec OpenApi',
            ],
            eng: [
              'Creation of a photo sales website',
              'Design and implementation of a REST API with OpenApi',
              'Conception et réalisation d\'une API REST avec OpenApi',
            ]
          }"
          :links="[
            { label: 'Front-end', link: 'https://www.vanbutselediane.com/' },
            { label: 'Back-end', link: 'https://diane-eshop.onrender.com/api' },
          ]"
        />
      </div>

      <div id="caroussel-item">
        <div id="item-wrapper">
          <div id="item-img">
            <img src="/muzikaloid_web.png" alt="">
          </div>
          <div id="item-content" @click="openModal" @closeModal="closeModal">
            <IconEye/>
            <div id="item-title">
              <h2>02/2023<br>06/2023</h2>
              <h1>Muzikaloid</h1>
            </div>
          </div>
        </div>

        <Modal 
          @closeModal="closeModal" 
          title="Muzikaloid" 
          date="02/23 - 06/23"
          :job="{
            fr: 'Développeur fullstack',
            eng: 'Fullstack developer'
          }"
          :tasks="
          {
            fr:           [
              'Création d’un forum sur la synthèse analogique musicale',
              'Conception d\'une API Rest avec OpenAPI',
              'Conception du front-end'
            ],
            eng: [
              'Creation of a forum on musical analog synthesis',
              'Design of a Rest API with OpenAPI',
              'Design of the front-end'
            ]
          }"
          :links="[
            // { label: 'Front-end', link: 'https://muzikaloid.onrender.com/' },
          ]"
        />
      </div>

      <div id="caroussel-item">
        <div id="item-wrapper">
          <div id="item-img">
            <img src="/visiteonline.png" alt="">
          </div>
          <div id="item-content" @click="openModal" @closeModal="closeModal">
            <IconEye/>

            <div id="item-title">
              <h2>05/2021<br>12/2022</h2>
              <h1>VisiteOnline</h1>
            </div>
          </div>
        </div>

        <Modal 
          @closeModal="closeModal" 
          title="VisiteOnline" 
          date="05/21 - 12/22"
          :job="{
            fr: 'Développeur fullstack',
            eng: 'Fullstack developer'
          }"
          :tasks="{
            fr: [
              'Création d’un outil de web-scraping',
              'Création d\'une API Rest avec OpenAPI',
              'Re factorisation et ajout de fonctionnalité sur un service d’import de données'
            ],
            eng: [
              'Creation of a web-scraping tool',
              'Creation of a Rest API with OpenAPI',
              'Refactoring and adding of new functionality to a data import service'
            ]
          }"
          :links="[]"
        />
      </div>

    </div>

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
  height: 35vh;
  background-color: var(--color-background-bis);
  margin:  32px 16px 16px 16px;
  border-radius: 8px;
}

#item-wrapper {
  height: 100%;
  width: 100%;
  transition: transform 200ms ease-in-out;
  cursor: pointer;
}

.active-item {
  transform: translate(8px, -8px);
}

#item-content > svg {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

#item-img {
  position: absolute;
  height: 100%;
  width: 100%;
  overflow: hidden;
  border-radius: 8px;
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
  border-radius: 0 0 8px 8px;
  z-index: 1;
  border-radius: 8px;
  display: flex;
  align-items: end;
}

#item-title {
  position: relative;
  height: 20%;
  width: 100%;
  background-color: var(--vt-c-black-bis);
  border-radius: 0 0 8px 8px;
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
    transform: translateY(0%);
  }

  #caroussel > div {
    width: 60vw;
    height: 30vh;
  }
}

@media (max-width: 425px) {

  #item-title {
    height: 25%;
  }

  #caroussel > div {
    width: 80vw;
    height: 25vh;
  }
}
</style>
