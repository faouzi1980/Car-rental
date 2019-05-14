<template>
  <section id="app">
    <transition name="fade" mode="out-in">
      <component v-on:nextComponent="currentComponent = 'Listing'" :is="currentComponent"></component>
    </transition>
  </section>
</template>

<script>
import Home from "./components/Home.vue";
import Listing from "./components/Listing.vue";

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

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s;
}
.fade-enter,
.fade-leave-to {
  opacity: 0;
}
</style>
