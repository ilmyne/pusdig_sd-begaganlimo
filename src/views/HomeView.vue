<template>
  <div class="home">
    <div class="container">
      <Navbar />
      <Hero />
      <div class="row mt-4">
        <div class="col">
          <h2>Most Wanted</h2>
        </div>
        <div class="col">
          <router-link to="/product">
            <b-button variant="primary" size="lg" class="float-right"
              >More</b-button
            >
          </router-link>
        </div>
      </div>

      <div class="row mb-4">
        <div
          class="col-md-4 mt-4"
          v-for="product in products"
          :key="product.id"
        >
          <CardProduct :product="product" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Hero from "@/components/Hero.vue";
import CardProduct from "@/components/CardProduct.vue";
import axios from "axios";
import Navbar from "@/components/Navbar.vue";

export default {
  name: "HomeView",
  components: {
    Hero,
    CardProduct,
    Navbar
},
  data() {
    return {
      products: [],
    };
  },
  methods: {
    setProduct(data) {
      this.products = data;
    },
  },
  mounted() {
    axios
      .get(" http://localhost:3000/Most-Wanted")
      .then((response) => this.setProduct(response.data))
      .catch((error) => console.log(error));
  },
};
</script>
