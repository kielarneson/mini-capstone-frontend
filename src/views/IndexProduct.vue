<template>
  <div class="index">
    <div v-for="product in products" v-bind:key="product.id">
      <h1>{{ product.name }}</h1>
      <img :src="product.primary_image" alt="" />
      <h2>{{ product.price }}</h2>
      <router-link v-bind:to="`/products/${product.id}`">More Info</router-link>
    </div>
  </div>
</template>

<style>
img {
  width: 400px;
}
</style>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      products: {},
    };
  },
  created: function () {
    this.indexProduct();
  },
  methods: {
    indexProduct: function () {
      axios.get("/products").then((response) => {
        console.log("Index Product", response.data);
        this.products = response.data;
        this.images = response.data.images;
      });
    },
  },
};
</script>
