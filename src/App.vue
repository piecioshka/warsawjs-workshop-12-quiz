<template>
  <div id="app">
    <img src="./assets/logo.png">
    <the-header></the-header>

    <router-view/>
  </div>
</template>

<script>
import TheHeader from './components/the-header.vue';

export default {
  name: 'app',
  components: {
    TheHeader
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
