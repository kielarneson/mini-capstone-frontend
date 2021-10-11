<template>
  <div class="show-product">
    <h2>{{ product.name }}</h2>
    <div v-for="image in images" v-bind:key="image.id">
      <img :src="image.url" alt="" />
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
