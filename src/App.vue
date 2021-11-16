<template>
  <div id="app">
    <div class="title-container">
      <logo-svg />
    </div>
    <card />
  </div>
</template>

<script>
import Card from './components/Card.vue'
import LogoSvg from './components/ui/LogoSvg.vue'
export default {
  name: 'App',
  components: {
    Card,
    LogoSvg,
  },
}
</script>

<style>
#app {
  margin: 20px 0;
  display: flex;
  flex-direction: column;
  width: 100vw;
  min-height: 100vh;
  justify-content: center;
  align-items: center;
}

.title-container {
  margin-bottom: 40px;
}
</style>
