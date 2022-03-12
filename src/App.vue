<template>
  <Header>
  <Main/>
</template>

<script>

import Header from "./components/HeaderSpotify.vue";
import Main from "./components/MainSpotify.vue";

export default {
  name: 'App',
  components: {
    Header,
    Main,

  }
}
</script>

<style lang="scss">
#app {
  max-width: 1970px;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
