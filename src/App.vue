<script setup>
// Cheat Sheet: https://steve-fallet.notion.site/Vue-3-script-setup-Cheat-Sheet-b12192ceae244ecda65f771579ca02bc
import {ref, onMounted} from 'vue'
import PageFooter from "@/components/PageFooter.vue";
import PageTopBar from "@/components/PageTopBar.vue";
import TroupeCarte from "@/components/TroupeCarte.vue";
/* Données */
// Total Or
const totalOr = ref(17478)
// Tableau des troupes
const troupes = ref([])
// Tableau des troupes formées
const troupesFormees = ref([])

/* Méthodes */
function formerTroupe(troupe) {
  if (totalOr.value < troupe.cout) {
    alert("Vous n'avez pas assez d'or mon seigneur !")
    return
  }
  totalOr.value -= troupe.cout
  troupesFormees.value.push(troupe)
}

/* Cycle de vie du composant */
// Quand le composant est monté, on va chercher les données
onMounted(() => {
  fetch('https://cocapi.divtec.me/troupes')
      .then((res) => res.json()) // Transforme le JSON en JavaScript
      .then((data) => { // Récupère les données (data) et les mets dans le tableau des troupes
        troupes.value = data
      })
})
</script>

<template>
  <page-top-bar :or="totalOr" :troupes="troupesFormees"/>
  <header>
    <h1>
      <img src="/img/clash-of-clans-logo.webp" alt="Logo Clash of Clans">
    </h1>
    <p class="description">
      Construire un village,
      former un clan et participer à des guerres de clans épiques !
    </p>
  </header>
  <main>
    <ul class="cartes">
      <li
        v-for="laTroupe in troupes"
        :key="laTroupe.id"
      >
        <troupe-carte :troupe="laTroupe"
                      :or="totalOr"
                      @former="formerTroupe"/>
      </li>
    </ul>
  </main>
  <page-footer />
</template>

<style scoped lang="sass">

</style>
