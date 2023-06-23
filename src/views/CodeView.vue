<script setup lang="ts">
import { inject, toRef } from 'vue';

const lang = toRef(inject('lang'));

</script>

<template>
  <main>
    <div class="about">
      <span class="title">
        <h1 class="date" v-if="lang === 'fr'">02/2021 - Aujourd'hui</h1>
        <h1 class="date" v-else>02/2021 - Today</h1>
        <h1 class="company">Muzikaloïd</h1>
        <h1 class="job" v-if="lang === 'fr'">Développeur fullstack</h1>
        <h1 class="job" v-else>Fullstack developer</h1>
      </span>
      <ul v-if="lang === 'fr'">
        <li>Création d’un forum sur la synthèse analogique musical</li>
        <li>Conception d'API Rest avec OpenAPI</li>
        <li>Conception  du <a href="https://muzikaloid.onrender.com/" target="_blank">front-end</a></li>
      </ul>
      <ul v-else>
        <li>Creation of a forum on musical analog synthesis</li>
        <li>Design of a Rest API with OpenAPI</li>
        <li>Design of the <a href="https://muzikaloid.onrender.com/" target="_blank">front-end</a></li>
      </ul>
    </div>
    <div class="about">
      <span class="title">
        <h1 class="date">04/2021 - 06/2022</h1>
        <h1 class="company">Particulier</h1>
        <h1 class="job" v-if="lang === 'fr'">Développeur fullstack</h1>
        <h1 class="job" v-else>Fullstack developer</h1>      </span>
      <ul v-if="lang === 'fr'">
        <li>Création d’un site de vente de photo</li>
        <li>Conception et réalisation d’une <a href="https://diane-eshop.onrender.com" target="_blank">API REST</a>
          avec OpenApi
        </li>
        <li>Conception et réalisation du <a href="https://vanbutselediane.com/" target="_blank">front-end</a></li>
      </ul>
      <ul v-else>
        <li>Creation of a photo sales website</li>
        <li>Design and implementation of a <a href="https://diane-eshop.onrender.com" target="_blank">REST API</a> with OpenApi</li>
        <li>Design and implementation of the <a href="https://vanbutselediane.com/" target="_blank">front-end</a></li>
      </ul>
    </div>
    <div class="about">
      <span class="title">
        <h1 class="date">05/2021 - 12/2022</h1>
        <h1 class="company">VisiteOnline</h1>
        <h1 class="job" v-if="lang === 'fr'">Développeur fullstack</h1>
        <h1 class="job" v-else>Fullstack developer</h1>      </span>
      <ul v-if="lang === 'fr'">
        <li>Création d’un outil de web-scraping</li>
        <li>Création d'API Rest avec OpenAPI</li>
        <li>Re factorisation et ajout de fonctionnalité sur un service d’import de données</li>
      </ul>
      <ul v-else>
        <li>Creation of a web-scraping tool</li>
        <li>Creation of a Rest API with OpenAPI</li>
        <li>Refactoring and adding of new functionality to a data import service</li>
      </ul>
    </div>
  </main>
</template>

<style scoped>
main {
  margin: 0 10vw;
  height: fit-content;
  padding: 16px;
  display: flex;
  flex-direction: column;
}

.about {
  color: var(--color-heading);
}

a {
  color: var(--color-text);
  text-decoration: underline;
  font-weight: bolder;
}

a:hover {
  background-color: var(--color-hover);
}

.about:not(:last-child) {
  margin-bottom: 16px;
}

.date {
  background-color: var(--color-text);
  color: var(--color-background);
  padding: 0 4px;
}

.job {
  background-color: var(--color-heading);
  color: var(--color-background);
  padding: 0 4px;
}

.title {
  width: 100%;
  display: flex;
  justify-content: space-between;
  color: var(--color-text);
}

h1 {
  font-weight: bolder;
}

li {
  font-weight: bolder;
}

@media (max-width: 768px) {
  main {
    margin: 0;
  }

  .title {
    flex-direction: column;
  }

  p {
    font-size: 1rem;
  }
}
</style>
