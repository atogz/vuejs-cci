<template>
  <div id="app">
    <ProductCart />
  </div>
</template>

<script>
import ProductCart from "./components/ProductCart";

export default {
  name: 'App',
  components: {
    ProductCart
  },
}
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
