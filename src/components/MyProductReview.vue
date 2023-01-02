<template>
  <div>
    <form @submit.prevent="onSubmit">
      <p v-if="errors.length">
        <span class="fw-bold">Please correct the following errors(s)</span>
        <ul>
          <li v-for="(error, index) in errors" :key="index">
          {{ error }}
          </li>
        </ul>
      </p>
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
      errors:[]
    };
  },
  methods: {
    onSubmit() {

      if(this.formData.name && this.formData.review && this.formData.rating){
        this.$emit("review-submited", this.formData);
      }
      else {
        if(!this.formData.name) this.errors.push('Name is required')
        if(!this.formData.review) this.errors.push('Review is required')
        if(!this.formData.rating) this.errors.push('Rating is required')
      }
     
    },
  },
};
</script>

<style></style>
