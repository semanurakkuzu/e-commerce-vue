<template>
  <div>
    <form @submit.prevent="onSubmit">
      <div class="mb-3">
        <label for="name" class="form-label">Name:</label>
        <input
          type="text"
          id="name"
          class="form-control"
          v-model="formData.name"
        />
      </div>
      <div>
        <label for="review">Review:</label>
        <textarea
          class="form-control"
          id="review"
          style="height: 100px"
          v-model="formData.review"
        ></textarea>
      </div>
      <div>
        <label for="review">Rating:</label>
      <select
        class="form-select mt-3"
        id="rating"
        aria-label="Default select example"
        v-model.number="formData.rating"
      >
        <option value="1">One</option>
        <option value="2">Two</option>
        <option value="3">Three</option>
      </select>
    </div>
      <div class="mt-3">
        <button type="submit" class="btn btn-primary container-fluid">Submit</button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "MyProductReview",
  data() {
    return {
      formData: {
        name: null,
        review: null,
        rating: null,
      },
    };
  },
  methods: {
    onSubmit() {
      this.$emit("review-submited", this.formData);
    },
  },
};
</script>

<style></style>
