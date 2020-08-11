<template>
  <div id="app">
    <Navigation />
    <router-view class="container" />
    <Footer/>
  </div>
</template>

<script>
import Navigation from '@/components/Navigation.vue'
import Footer from '@/components/Footer.vue'
export default {
  name: 'app',
  components: {
    Navigation,
    Footer
  }
}
</script>

<style lang="scss">
$primary: #304455;
@import "node_modules/bootstrap/scss/bootstrap";
</style>
