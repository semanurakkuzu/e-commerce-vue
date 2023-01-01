<template>
  <div id="app">
    <my-product></my-product>
  </div>
</template>

<script>
import MyProduct from './components/MyProduct.vue'


export default {
  name: 'App',
  components: {
    MyProduct
    
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
