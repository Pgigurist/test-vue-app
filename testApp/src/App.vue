<template>
  <div id="app">
    <img src="./assets/logo.png">
    <user/>
    <router-view/>
  </div>
</template>

<script>

import user from './components/User.vue'

export default {
    name: 'App',
    components: {
        user
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
