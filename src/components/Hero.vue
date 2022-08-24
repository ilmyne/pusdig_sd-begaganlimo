<template>
  <div class="hero">
    <!-- Desktop -->
    <div class="d-none d-md-block">
      <div class="row mt-4">
        <div class="col-md-6">
          <div class="d-flex h-100">
            <div class="justify-content-center align-self-center">
              <h2>
                <strong>Welcome</strong><br />Place for your daily drive with
                best deal
              </h2>
              <div>
                <router-link to="/product">
                  <b-button variant="primary" size="lg">Buy Now</b-button>
                </router-link>
              </div>
            </div>
          </div>
        </div>
        <div class="col">
          <img src="../assets/img/model1.jpg" width="100%" />
        </div>
      </div>
    </div>

    <!-- Mobile -->
    <div class="d-sm-block d-md-none">
      <div class="row mt-4">
        <div class="col-md-6 mb-3">
          <img src="../assets/img/model1.jpg" width="100%" />
        </div>
        <div class="col-md-6">
          <div class="d-flex h-100">
            <div class="justify-content-center align-self-center">
              <h2>
                <strong>Welcome</strong><br />Place for your daily drive with
                best deal
              </h2>
              <!-- <button class="btn btn-lg btn-success">Buy Now</button> -->
              <b-button variant="primary" size="lg">Buy Now</b-button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Hero",
};
</script>

<style>
</style>