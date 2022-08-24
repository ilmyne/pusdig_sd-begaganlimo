<template>
  <div class="card shadow card-product">
    <img :src="'assets/img/' + product.gambar" class="card-img-top" alt="" />
    <div class="card-body">
      <h5 class="card-title">{{ product.nama }}</h5>
      <p class="card-text">Harga : Rp. {{ product.harga }}</p>
      <router-link :to="'/product/'+product.id">
        <b-button variant="primary" size="lg" class="buy"
          >See Specification</b-button
        >
      </router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: "CardProduct",
  props: ["product"],
};
</script>

<style>
</style>