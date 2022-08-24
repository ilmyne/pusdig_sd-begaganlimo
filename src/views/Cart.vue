<template>
  <div class="cart">
    <Navbar :updateCart="carts"/>
    <div class="container">
      <!-- bikin kotakan abu di atas yg ada tulisannya home > product > cart -->
      <div class="row mt-4">
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
              <li class="breadcrumb-item active" aria-current="page">Cart</li>
            </ol>
          </nav>
        </div>
      </div>

      <div class="row">
        <div class="col">
          <div class="table-responsive mt-3">
            <table class="table">
              <thead>
                <tr>
                  <th scope="col">No.</th>
                  <th scope="col">Product</th>
                  <th scope="col">Details Specification</th>
                  <th scope="col">Price</th>
                  <th scope="col">Quantity</th>
                  <th scope="col">Total Price</th>
                  <th scope="col">Remove</th>
                </tr>
              </thead>
              <tbody>
                <!-- product detailnya -->
                <tr v-for="(cart, index) in carts" :key="cart.id">
                  <th>{{ index + 1 }}</th>
                  <td>
                    <strong>{{ cart.products.nama }}</strong>
                    <br />
                    <img
                      :src="'../assets/img/' + cart.products.gambar"
                      class="img-fluid shadow"
                      width="250"
                    />
                  </td>
                  <td>
                    <strong>{{ cart.products.specification }}</strong>
                  </td>

                  <td align="center">Rp.{{ cart.products.harga }}</td>
                  <td align="center">{{ cart.quantity }}</td>
                  <td align="center">
                    <strong
                      >Rp. {{ cart.products.harga * cart.quantity }}</strong
                    >
                  </td>
                  <td align="center" class="text-danger">
                    <button @click="deleteItem(cart.id)">
                      <b-icon-trash></b-icon-trash>
                    </button>
                  </td>
                </tr>

                <!-- totalan -->
                <tr>
                  <td colspan="5" align="right">
                    <strong>Price Total: </strong>
                  </td>
                  <td>
                    <strong>Rp. {{ priceTotal }} </strong>
                  </td>
                  <td></td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Navbar from "@/components/Navbar.vue";
import axios from "axios";
export default {
  name: "1",
  components: {
    Navbar,
  },
  data() {
    return {
      carts: [],
    };
  },
  methods: {
    setCarts(data) {
      this.carts = data;
    },
    deleteItem(id) {
      axios
      .delete("http://localhost:3000/Cart/" + id)
      .then(() => {
        this.$toast.error("Item deleted", {
          type: "error",
          position: "top-right",
          duration: 500,
          dismissible: true,
        });
        // mengupdate halaman setelah dihapus dengan memanggil API Cart
        axios
    .get("http://localhost:3000/Cart")
    .then((response) => this.setCarts(response.data))
    .catch((error) => console.log(error));
      });
    },
  },
  mounted() {
    axios
      .get("http://localhost:3000/Cart")
      .then((response) => this.setCarts(response.data))
      .catch((error) => console.log(error));
  },
  computed: {
    priceTotal() {
      return this.carts.reduce(function (items, data) {
        return items + data.products.harga * data.quantity;
      }, 0);
    },
  },
};
</script>