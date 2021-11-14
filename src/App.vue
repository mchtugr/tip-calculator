<template>
  <div id="app">
    <div>
      <h3>SPLIT</h3>
      <h3>TTER</h3>
    </div>
    <card />
  </div>
</template>

<script>
import Card from './components/Card.vue'
export default {
  name: 'App',
  components: {
    Card,
  },
}
</script>

<style>
#app {
  display: flex;
  flex-direction: column;
  width: 100vw;
  height: 100vh;
  justify-content: center;
  align-items: center;
}
</style>
