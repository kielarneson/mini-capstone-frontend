<template>
  <div class="index">
    <div v-for="product in products" v-bind:key="product.id">
      <h1>{{ product.name }}</h1>
      <h2>{{ product.price }}</h2>
      <router-link v-bind:to="`/products/${product.id}`">More Info</router-link>
    </div>
  </div>
</template>

<style></style>

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
        console.log("Index Product", response);
        this.products = response.data;
      });
    },
  },
};
</script>
