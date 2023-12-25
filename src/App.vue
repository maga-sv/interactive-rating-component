<script setup>
import Card from './components/card/Card.vue';

</script>

<template>
  <main>
      <section class="rating">

        <div class="container">

          <Card />

        </div>

      </section>
  </main>
</template>

<style scoped>

main {
  min-height: 100vh;
  height: 100%;
  display: grid;
  place-items: center;
}
</style>
