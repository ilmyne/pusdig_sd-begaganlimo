<template>
  <div class="hero">
    <!-- Desktop -->
    <div class="d-none d-md-block">
      <div class="row mt-4">
        <div class="col-md-6">
          <div class="d-flex h-100">
            <div class="justify-content-center align-self-center">
            </div>
          </div>
        </div>
      </div>
      <div>
        <v-row align="center">
  <b-card
    overlay
    img-src="https://picsum.photos/900/250/?image=5"
    img-alt="Card Image"
    text-variant="white"
    title="DevGear"
    sub-title=""
  >
    <b-card-text>
      <v-row align="center">
        <br>
        <h6>
        DevGear is passionate about technology and driven by innovation.
        <br>
        We dream, we dare and we strive to create an effortless and joyful digital life for everyone. 
        <br>
        We're always in search of incredible ideas and experiences,
        <br>
        and we aspire to deliver the incredible in everything we do.
        <br>
        Was made in 2022, inspired by dev geeks who needs support device in best quality with best deal
      </h6>
      </v-row>
    </b-card-text>
  </b-card>
  </v-row>
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
  name: "Hero3",
};
</script>

<style>
</style>