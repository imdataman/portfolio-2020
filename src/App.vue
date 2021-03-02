<template>
  <div id="app">
    <div class="lang">
      <svg width="65px" height="40px" @click="changeLang">
        <circle
          v-once
          id="button"
          :cx="lang === 'zhTW' ? 16 : 46"
          cy="22.5"
          r="15"
          stroke="black"
          fill="white"
        ></circle>
        <text x="16" y="24.5">中</text>
        <text x="46" y="24.5">E</text>
      </svg>
    </div>
    <About :lang="lang" />
    <Work :lang="lang" />
    <footer>
      <small>&copy; Copyright 2021, Chia-Hsien (Andy) Lin </small>
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
  },
  data() {
    return {
      lang: /zh/.test(navigator.language || navigator.userLanguage)
        ? "zhTW"
        : "en"
    };
  },
  methods: {
    changeLang() {
      let transformTo = "";
      if (/zh/.test(navigator.language || navigator.userLanguage)) {
        transformTo =
          this.lang === "zhTW" ? "translate(30px, 0px)" : "translate(0px, 0px)";
      } else {
        transformTo =
          this.lang === "zhTW"
            ? "translate(0px, 0px)"
            : "translate(-30px, 0px)";
      }
      document.getElementById("button").style.transform = transformTo;
      this.lang = this.lang === "zhTW" ? "en" : "zhTW";
    }
  }
};
</script>

<style lang="scss">
svg {
  cursor: pointer;
  text {
    text-anchor: middle;
    dominant-baseline: middle;
    pointer-events: none;
  }
  circle {
    -moz-transition: all 0.2s ease-in-out;
    -o-transition: all 0.2s ease-in-out;
    -webkit-transition: all 0.2s ease-in-out;
    transition: all 0.2s ease-in-out;
  }
}

.lang {
  margin-top: 0.5rem;
}

body {
  margin: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif, "Microsoft JhengHei";
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
