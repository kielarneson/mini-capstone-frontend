<template>
  <div class="index">
    <div v-for="product in products" v-bind:key="product.id">
      <h1>{{ product.name }}</h1>
      <p>{{ product.description }}</p>
      <p>{{ product.price }}</p>
      <p>{{ product.supplier.name }}</p>
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
