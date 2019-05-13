<template>
  <section class="section" id="app">
    <component :is="currentComponent"></component>    
  </section>
</template>

<script>
import Home from "./components/Home.vue";

export default {
  name: "app",
  data(){
    return{
      currentComponent: "Home"
    }
  },
  components: {
    Home
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
