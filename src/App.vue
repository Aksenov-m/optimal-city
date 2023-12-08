<script setup>
import Container from './components/Container.vue';

</script>

<template>
  <div id="app-container">
    <Container />
  </div>
</template>

<style>

#app-container {
  min-height: 100vh; /* Минимальная высота всей страницы */
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
}
</style>
