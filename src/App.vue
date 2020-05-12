<template>
  <div id="app">
    <About />
    <Work />
    <footer>
      <small>&copy; Copyright 2020, Andy Lin Chia Hsien</small>
    </footer>
  </div>
</template>

<script>
import Work from "./components/Work.vue";
import About from "./components/About.vue";

export default {
  name: "App",
  components: {
    About,
    Work
  }
};
</script>

<style lang="scss">
body {
  margin: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 80vw;
  max-width: $max-width;
  margin: 0 auto;
}

footer {
  text-align: center;
  margin-bottom: 10px;
  opacity: $subtitle-opacity;
}
</style>
