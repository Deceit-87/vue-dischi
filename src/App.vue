<template>
  <div id="app">
    <Header/>
    <Main/>
  </div>
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
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
body{
  background-color: #1e2d3b;
  max-width: 1970px;
  height: 100vh;
}
ul,ol{
  list-style: none;
}

 * img{
  max-width: 100%;
}
</style>
