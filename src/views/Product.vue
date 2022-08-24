<template>
  <div class="product">
    <div class="container">
      <Navbar />
      <Hero2 />

      <div class="row mt-5">
        <div class="col">
          <b-form-input
            placeholder="Search your preference"
            v-model="search" @keyup="searchProduct"
          ></b-form-input>
        </div>
      </div>

      <!-- untuk nampilin card nya -->
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
import Hero2 from "@/components/Hero2.vue";
import CardProduct from "@/components/CardProduct.vue";
import axios from "axios";
import Navbar from "@/components/Navbar.vue";

export default {
  name: "Product",
  components: {
    Hero2,
    CardProduct,
    Navbar
},
  data() {
    return {
      products: [],
      search: "",
    };
  },
  methods: {
    setProduct(data) {
      this.products = data;
    },
    searchProduct() {
      axios
        .get(" http://localhost:3000/Products?q=" + this.search)
        .then((response) => this.setProduct(response.data))
        .catch((error) => console.log(error));
    },
  },
  mounted() {
    axios
      .get(" http://localhost:3000/Products")
      .then((response) => this.setProduct(response.data))
      .catch((error) => console.log(error));
  },
};
</script>

<style>
</style>