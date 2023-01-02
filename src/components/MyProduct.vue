<template>
  <div>
    <div class="row mt-5">
      <div class="col-4 ml-5">
        <img :src="image" style="width: 400px; height: 600px" />
      </div>
      <div class="col">
        <h1>{{ title }}</h1>
        <p v-if="inStock">In stock</p>
        <p v-else>Out of stock</p>
        <p>Shipping: {{ shipping }}</p>
        <ul>
          <li v-for="(item, index) in details" :key="index">{{ item }}</li>
        </ul>
        <div
          v-for="(variant, index) in variants"
          :key="variant.variantId"
          class="box-size"
          :style="{ backgroundColor: variant.variantColor }"
          @mouseover="updateProduct(index)"
        ></div>
        <div class="row">
          <div class="col-auto">
            <button
              class="btn btn-primary"
              @click="addToCart"
              :disabled="!inStock"
            >
              Add to Cart
            </button>
          </div>
        </div>
      </div>
    </div>
    <div>
      <h2>Reviews</h2>
      <p v-if="!reviews.length">There are no reviews yet!</p>
      <ul>
        <li v-for="(review, index) in reviews" :key="index">
        <p>{{ review.name }}</p>
        <p>Rating:{{ review.rating }}</p>
        <p>{{ review.review }}</p>
      </li>
      </ul>

    </div>
    <div class="card p-2">
      <my-product-review @review-submited="addReview"></my-product-review>
    </div>
  </div>
</template>

<script>
import MyProductReview from "./MyProductReview.vue";
export default {
  name: "MyProduct",
  components: {
    MyProductReview,
  },
  props: {
    premium: {
      type: Boolean,
      required: true,
    },
  },
  data() {
    return {
      brand: "Vue Mastery",
      product: "socks",
      selectVariants: 0,
      details: ["80% cotton", "20% polyester", "Gender-Neutral"],
      variants: [
        {
          variantId: 11,
          variantColor: "red",
          variantImage:
            "https://cdn.shopify.com/s/files/1/1409/0762/products/Red_Cloud_SOck_copy_800x.jpg?v=1645761997",
          variantQuantity: 10,
        },
        {
          variantId: 22,
          variantColor: "purple",
          variantImage:
            "https://cdn.shopify.com/s/files/1/1409/0762/products/CloudSockinEggplant_800x.png?v=1645761997",
          variantQuantity: 0,
        },
      ],
      reviews: [],
    };
  },
  computed: {
    title() {
      return this.brand + " " + this.product;
    },
    image() {
      return this.variants[this.selectVariants].variantImage;
    },
    inStock() {
      return this.variants[this.selectVariants].variantQuantity;
    },
    shipping() {
      if (this.premium) {
        return "Free";
      }
      return "2.99";
    },
  },

  methods: {
    updateProduct(index) {
      this.selectVariants = index;
    },
    addToCart() {
      this.$emit("add-to-cart", this.variants[this.selectVariants].variantId);
    },
    addReview(formData) {
      this.reviews.push(formData);
    },
  },
};
</script>

<style>
.box-size {
  width: 40px;
  height: 40px;
  margin: 5px;
}
</style>
