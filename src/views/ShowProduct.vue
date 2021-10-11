<template>
  <div class="show-product">
    <div class="container">
      <div class="row">
        <div class="col">
          <h2>{{ product.name }}</h2>
          <div id="carouselExampleControls" class="carousel carousel-dark slide" data-bs-ride="carousel">
            <div class="carousel-inner">
              <div
                class="carousel-item"
                v-for="(image, idx) in images"
                v-bind:key="image.id"
                :class="{ active: idx == 0 }"
              >
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
        </div>
        <div class="col">
          <h3>{{ this.price }}</h3>
          <p class="description">{{ product.description }}</p>
          <router-link to="/products">Return to Products</router-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      product: {},
      images: {},
      price: {},
    };
  },
  created: function () {
    axios.get(`products/${this.$route.params.id}`).then((response) => {
      console.log("Show Product", response);
      this.product = response.data;
      this.images = response.data.images;
      this.price = response.data.price;
      this.description = response.data.description;

      if (this.price.slice(5, 7) == 99) {
        this.price = "$" + this.price.slice(0, 1) + "," + this.price.slice(1, 7);
      }
    });
  },
  methods: {},
};
</script>
