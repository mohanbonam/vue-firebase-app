<template>
  <div class="mt-3">
    <div class="container text-center">
      <div class="row justify-content-center">
        <div class="col-10 col-md-10 col-lg-8 col-xl-7">
          <p class="lead">
            Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
            <br><i class="fas fa-meteor fa-2x mt-3"></i>
          </p>

          <router-link
            class="btn btn-outline-primary mr-2"
            to="/register"
            v-if="!user"
          >Register</router-link>
          <router-link
            class="btn btn-outline-primary mr-2"
            to="/login"
            v-if="!user"
          >Log In</router-link>
          <router-link
            class="btn btn-primary"
            to="/secret"
            v-if="user"
          >Secret Content</router-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Home',
  props: ['user']
}
</script>

<style lang="scss">

</style>
