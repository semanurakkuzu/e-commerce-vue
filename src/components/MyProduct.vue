<template>
  <div>
    <div class="row mt-5">
      <div class="col-4 ml-5">
        <img :src="image" style="width: 400px; height: 600px" />
      </div>
      <div class="col">
        <h1>{{ product }}</h1>
        <p v-if="inStock">In stock</p>
        <p v-else>Out of stock</p>
        <ul>
          <li v-for="(item, index) in details" :key="index">{{ item }}</li>
        </ul>
        <div v-for="variant in variants" :key="variant.variantId" class="box-size"
        :style="{backgroundColor:variant.variantColor}"
        @mouseover="updateProduct(variant.variantImage)">
        </div>
        <div class="row">
          <div class="col-auto">
            <button class="btn btn-primary" @click="cart=cart+1" :disabled="!inStock">Add to Cart</button>
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
      inStock: true,
      details: ["80% cotton", "20% polyester", "Gender-Neutral"],
      variants: [
        {
          variantId: 1,
          variantColor: "red",
          variantImage:"https://cdn.shopify.com/s/files/1/1409/0762/products/Red_Cloud_SOck_copy_800x.jpg?v=1645761997"
        },
        {
          variantId: 2,
          variantColor: "purple",
          variantImage:"https://cdn.shopify.com/s/files/1/1409/0762/products/CloudSockinEggplant_800x.png?v=1645761997"
        },
      ],
      cart: 0,
    }
  },
   methods:{
    updateProduct(variantImage){
      this.image=variantImage
    }
   },
  
};
</script>

<style>
.box-size {
    width:40px; 
    height:40px;
    margin: 5px;
}
</style>
