<template>
  <div id="app">
    <router-view/>
    <footeer/>
  </div>
</template>

<script>
  import footeer from "../src/mainComponents/footer";
  export default {
    components:{
      footeer
    }
  }
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    color: black;
    height: 100vh;
    width: 100vw;
    background-color: white;
  }

  li{
    list-style-type: none;
  }

  a{
    text-decoration: none;
  }
</style>
