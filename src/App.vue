<script setup>
// Cheat Sheet: https://steve-fallet.notion.site/Vue-3-script-setup-Cheat-Sheet-b12192ceae244ecda65f771579ca02bc
import {ref} from 'vue'

// Tableau des troupes
const troupes = ref([
  {
    "id": 2,
    "nom": "Archer",
    "niveau": 3,
    "formation": 25,
    "vitesse": 24,
    "cout": 200,
    "description": "Les archers sont des tireurs d'élite qui attaquent à distance. Ils sont rapides et bon marché à former, mais ils sont faibles en mêlée et doivent être protégés.",
    "couleur": "#EE5487",
    "image": "https://cocapi.divtec.me/img/archer.png"
  },
  {
    "id": 1,
    "nom": "Barbare",
    "niveau": 4,
    "formation": 20,
    "vitesse": 16,
    "cout": 150,
    "description": "Ce guerrier intrépide compte sur ses muscles saillants et sa fière moustache pour semer le chaos dans les villages ennemis. Faites charger une horde de barbares et profitez du spectacle !",
    "couleur": "#ebb428",
    "image": "https://cocapi.divtec.me/img/barbare.png"
  },
  {
    "id": 3,
    "nom": "Géant",
    "niveau": 5,
    "formation": 12,
    "vitesse": 12,
    "cout": 2250,
    "description": "Les géants sont de grands guerriers qui attaquent les défenses ennemies en premier. Ils sont lents mais résistants.",
    "couleur": "#F6901A",
    "image": "https://cocapi.divtec.me/img/geant.png"
  }
])
</script>

<template>
  <h1>Clash Of Clans</h1>
  <ul>
    <li
        v-for="troupe in troupes"
        :key="troupe.id"
        :style="`background-color: ${troupe.couleur};`"
    >
      {{ troupe.nom }}
      <img :src="troupe.image" :alt="troupe.nom">
    </li>
  </ul>
</template>

<style scoped>

</style>
