<template>
  <div class="show-product">
    <h2>{{ product.name }}</h2>
    <p>{{ product.description }}</p>
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
    };
  },
  created: function () {
    axios.get(`products/${this.$route.params.id}`).then((response) => {
      console.log("Show Product", response);
      this.product = response.data;
    });
  },
  methods: {},
};
</script>
