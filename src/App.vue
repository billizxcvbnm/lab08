<template>
  <div id="app">
     <!-- <router-link to="/">Home</router-link>|-->
      <!--<router-link to="/about">About</router-link>-->
    <bodyslam />
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
import bodyslam from "./components/bodyslam.vue";

export default {
  name: "App",
  components: {
    bodyslam,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
