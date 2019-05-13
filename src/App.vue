<template>
  <section class="section" id="app">
    <component v-on:next="currentComponent = 'Listing'" :is="currentComponent"></component>
  </section>
</template>

<script>
import Home from "./components/Home.vue";
import Listing from "./components/Listing.vue";
import { serverBus } from "./main";

export default {
  name: "app",
  data() {
    return {
      currentComponent: "Home"
    };
  },
  methods: {
    nextSection() {
      this.currentComponent = "Listing";
    }
  },
  components: {
    Home,
    Listing
  },
  created() {
    serverBus.$on("nextComponent", val => {
      this.currentComponent = val;
    });
  }
};
</script>

<style>
* {
  font-family: "Product sans", Helvetica, Arial, sans-serif;
}

.mBottom20 {
  margin-bottom: 2rem;
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
