<template>
  <div id="app" class="container">
    <div class="d-flex justify-content-end">
      <p class="bg-primary p-2 text-white">Cart:{{ cart.length }}</p>
    </div>
    <my-product :premium="premium" @add-to-cart="updateCard"></my-product>
  </div>
</template>

<script>
import MyProduct from "./components/MyProduct.vue";
export default {
  name: "App",
  components: {
    MyProduct,
  },
  data() {
    return {
      premium: true,
      cart: [],
    };
  },
  methods: {
    updateCard(id) {
      this.cart.push(id);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
