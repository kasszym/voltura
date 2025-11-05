<script setup>
import Header from "./components/Header.vue";
import IntroComponent from "./components/MainPageComponents/IntroComponent.vue";
import CarRanges from "./components/CarRange.vue/CarRanges.vue";
</script>

<template>
  <div>
    <Header />
    <main
      class="container app-container px-0 d-flex flex-column"
      style="gap: 40px; margin: 32px auto"
    >
      <IntroComponent />
      <div><CarRanges /></div>
      <div><p>sekcja 3</p></div>
    </main>
  </div>
</template>
<style scoped>
.app-container {
  max-width: var(--app-width) !important;
  width: 100%;
}
</style>
