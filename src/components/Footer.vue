<template>
  <div style="margin-top: 12%; margin-left: 3%; margin-right: 3%" class="footer">
      <b-navbar-brand
        tag="h1"
        class="mb-0"
        href="/"
        type="black"
        style="font-family: 'Montserrat', sans-serif; font-size: xx-large"
        ><img src="../assets/img/logo2.png" alt=""
      /></b-navbar-brand>
    <div class="footer">
      <b-nav vertical class="w-25">
        <b-nav-item type="black" href="/">Home</b-nav-item>
        <b-nav-item type="black" href="product">Product</b-nav-item>
        <b-nav-item type="black" href="aboutview">About Us</b-nav-item>
      </b-nav>
    </div>

    <div class="footer">

      <b-row align-h="end" style="padding: 4% 0">
        <b-col cols="6">
          &copy;2022      <a href="/"><img src="../assets/img/logo2.png" alt="" /></a>Copyright
        </b-col>
        <b-col cols="2" align-self="start">
        </b-col>
      </b-row>
    </div>
    
  </div>
</template>

<script>
export default {
  name: "Footer",
};
</script>

<style>
.link-margin {
  margin: 0 3%;
}
</style>

