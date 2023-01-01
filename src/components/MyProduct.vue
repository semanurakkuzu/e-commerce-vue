<template>
  <div>
    <div class="row mt-5">
      <div class="col-4 ml-5">
        <img :src="image" style="width: 400px; height: 600px" />
      </div>
      <div class="col">
        <h1>{{ product }}</h1>
        <p v-if="stock > 10">In stock</p>
        <p v-else-if="stock <= 10 && stock > 0">Almost sold out!</p>
        <p v-else>Out of stock</p>
        <ul>
          <li v-for="(item, index) in details" :key="index">{{ item }}</li>
        </ul>
        <div v-for="variant in variants" :key="variant.variantId">
          <p>{{ variant.variantColor }}</p>
        </div>
        <div class="row">
          <div class="col-auto">
            <button class="btn btn-primary" @click="cart=cart+1">Add to Cart</button>
          </div>
          <div class="col">
            <p>Cart:{{ cart }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MyProduct",
  data() {
    return {
      product: "socks",
      image:
        "https://cdn.shopify.com/s/files/1/1409/0762/products/Red_Cloud_SOck_copy_800x.jpg?v=1645761997",
      stock: 0,
      details: ["80% cotton", "20% polyester", "Gender-Neutral"],
      variants: [
        {
          variantId: 1,
          variantColor: "red",
        },
        {
          variantId: 2,
          variantColor: "purple",
        },
      ],
      cart: 0,
    };
  },
};
</script>

<style></style>
