<template>
  <CoffeeShop msg="Welcome to Your Coffee Shop" />
</template>

<script>
import CoffeeShop from "./components/CoffeeShop.vue";

export default {
  name: "App",
  components: {
    CoffeeShop,
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
