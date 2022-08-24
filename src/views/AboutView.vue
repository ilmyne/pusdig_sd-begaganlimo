<template>
  <div class="home">
    <div class="container">
      <Navbar />
    <Hero3 />

    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Hero3 from '@/components/Hero3.vue'
import Navbar from '@/components/Navbar.vue'

export default {
  name: 'AboutView',
  components: {
    Hero3,
    Navbar
}
}
</script>
