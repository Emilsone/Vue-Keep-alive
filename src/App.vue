<template>
  <div id="app">
    <General  />
    <!-- <GetPage /> -->
  </div>
</template>

<script>
import General from "./components/General.vue";
// import PostPage from "./components/PostPage.vue";

export default {
  name: "App",
  components: {
    General,
    // PostPage,
  },
   



 
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Open+Sans:wght@300&display=swap");

#app {
  font-family: "Open Sans", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
