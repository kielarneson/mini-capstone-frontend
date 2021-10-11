<template>
  <div class="index">
    <div v-for="product in products" v-bind:key="product.id">
      <router-link v-bind:to="`/products/${product.id}`">
        <h2>{{ product.name }}</h2>
        <img :src="product.primary_image" alt="" />
      </router-link>
      <h2>{{ product.price }}</h2>
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
