<template>
  <div class="product-detail">
    <Navbar />
    <div class="container">
      <!-- kotakan abu-abu -->
      <div class="row mt-5">
        <div class="col">
          <nav aria-label="breadcrumb">
            <ol class="breadcrumb">
              <li class="breadcrumb-item">
                <router-link to="/" class="text-dark">Home</router-link>
              </li>
              <li class="breadcrumb-item">
                <router-link to="/product" class="text-dark"
                  >Product</router-link
                >
              </li>
              <li class="breadcrumb-item active" aria-current="page">
                Product Specification
              </li>
            </ol>
          </nav>
        </div>
      </div>

      <!-- product detail -->

      <div class="row">
        <div class="col-md-6">
          <img
            :src="'../assets/img/' + product.gambar"
            class="img-fluid shadow"
          />
        </div>
        <div class="col-md-6">
          <h1>Specification</h1>
          <hr />
          <br />
          <h4>Product Name : {{ product.nama }}</h4>
          <h4>Price : {{ product.harga }}</h4>
          <h4>{{ product.specification }}</h4>
          <form class="mt-4" v-on:submit.prevent>
            <div class="form-group">
              <b-container fluid>
                <b-row class="my-1" v-for="type in types" :key="type">
                  <b-col sm="3">
                    <label for="quantity"> <h4>Quantity</h4></label>
                  </b-col>
                  <br />
                  <b-col sm="9">
                    <b-form-input
                      :id="`type-${type}`"
                      :type="type"
                      v-model="order.quantity"
                      class="form-control"
                      placeholder="Input Your Quantity"
                    ></b-form-input>
                  </b-col>
                </b-row>
              </b-container>
              <label for="note"> <h4>Recipient Name & Address</h4></label>
              <textarea
                v-model="order.note"
                class="form-control"
                placeholder="JaneDoe & Lorem Ipsum Street A26"
              ></textarea>
            </div>

            <b-button variant="primary" size="lg" class="buy" @click="buy"
              ><b-icon-cart></b-icon-cart>Add to Cart</b-button
            >
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Navbar from "@/components/Navbar.vue";
import axios from "axios";

export default {
  name: "ProductDetail",
  components: {
    Navbar,
  },
  data() {
    return {
      product: {},
      order: {},
      types: ["number"],
    };
  },
  methods: {
    setProduct(data) {
      this.product = data;
    },
    buy() {
      if (this.order.note) {
        this.order.products = this.product;
        axios
          .post("http://localhost:3000/Cart", this.order)
          .then(() => {
            this.$router.push({ path: "/cart" });
            this.$toast.success("Add to Cart!", {
              type: "success",
              position: "top-right",
              duration: 500,
              dismissible: true,
            });
          })
          .catch((err) => console.log(err));
      } else {
        this.$toast.error("Fill Your Order", {
          type: "error",
          position: "top-right",
          duration: 500,
          dismissible: true,
        });
      }
    },
  },
  mounted() {
    axios
      .get(" http://localhost:3000/Products/" + this.$route.params.id)
      .then((response) => this.setProduct(response.data))
      .catch((error) => console.log(error));
  },
};
</script>