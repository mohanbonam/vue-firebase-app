<template>
  <div>
    <nav class="navbar navbar-expand bg-primary navbar-dark">
      <div class="container-fluid">
        <router-link class="navbar-brand" to="/"><i class="fas fa-magic fa-lg mr-2"></i>M O H A N B O N A M</router-link>
        <div class="navbar-nav ml-auto">
          <router-link class="nav-item nav-link" to="/meetings">Meetings</router-link>
          <router-link class="nav-item nav-link" to="/register">Register</router-link>
          <router-link class="nav-item nav-link" to="/login">Login</router-link>
        </div>
      </div>
    </nav>
  </div>
</template>

<script>
export default {
  name: 'Navigation',
  data () {
    return {
    }
  },
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
</style>
