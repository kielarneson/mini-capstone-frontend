<template>
  <div class="show-product">
    <h2>{{ product.name }}</h2>

    <div id="carouselExampleControls" class="carousel slide" data-bs-ride="carousel">
      <div class="carousel-inner">
        <div class="carousel-item" v-for="(image, idx) in images" v-bind:key="image.id" :class="{ active: idx == 0 }">
          <img :src="image.url" alt="" class="img-fluid" />
        </div>
      </div>
      <button
        class="carousel-control-prev"
        type="button"
        data-bs-target="#carouselExampleControls"
        data-bs-slide="prev"
      >
        <span class="carousel-control-prev-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Previous</span>
      </button>
      <button
        class="carousel-control-next"
        type="button"
        data-bs-target="#carouselExampleControls"
        data-bs-slide="next"
      >
        <span class="carousel-control-next-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Next</span>
      </button>
    </div>
    <p>{{ product.description }}</p>
    <h3>{{ product.price }}</h3>
    <router-link to="/products">Return to Products</router-link>
  </div>
</template>

<style></style>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      product: {},
      images: {},
    };
  },
  created: function () {
    axios.get(`products/${this.$route.params.id}`).then((response) => {
      console.log("Show Product", response);
      this.product = response.data;
      this.images = response.data.images;
      console.log(this.images);
    });
  },
  methods: {},
};
</script>
