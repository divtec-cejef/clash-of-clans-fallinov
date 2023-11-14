<script setup>
defineProps({
  or: {
    type: Number,
    required: true
  },
  nbTroupesFormees: {
    type: Number,
    required: true
  }
})
</script>

<template>
  <aside class="solde-or">
    <div>
      <img src="/img/piece-or-note.jpg" alt="Solde Or">
      {{ or }} pièces d'or
    </div>
    <div>
      <img src="/img/troupes-icon.png" alt="Troupes">
      {{  nbTroupesFormees }} troupes formées
    </div>
  </aside>
</template>

<style scoped>

</style>
