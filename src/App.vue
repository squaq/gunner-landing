<template>
  <div id="app">
    <MainGunner msg="Welcome to Your Vue.js App"/>
    <TvScreen/>
  </div>
</template>

<script>
import MainGunner from './components/MainGunner.vue'
import TvScreen from './components/tv/TvScreen.vue'

export default {
  name: 'App',
  components: {
    MainGunner,
    TvScreen
  }
}
</script>

<style>
body {
  margin: 0;
  padding: 0;
  background: #1a1000;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
