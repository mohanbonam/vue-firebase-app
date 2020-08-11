<template>
  <div class="mt-3">
    <div class="text-secondary text-center">
      <div
        v-if="user"
        class="text-center"
      >
        Welcome back
        <span class="font-weight-bold text-info">{{user.displayName}}</span>, <a
          href="#"
          role="button"
          class="text-primary"
          @click="$emit('logout')"
        >logout</a>
      </div>
    </div>
    <div class="container text-center">
      <div class="row justify-content-center">
        <div class="col-10 col-md-10 col-lg-8 col-xl-7">
          <h4 class="display-4 text-primary mb-2">You are being watched</h4>
          <p class="lead">
            Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
            <br><i class="fas fa-meteor fa-2x mt-3"></i>
            <!-- This simple app creates meetings, allows people to check in, and
            picks random users to award giveaways. It's a good example of a
            Single Page Application which includes connection to a database and
            routing. It's a practical way to learn
            <a href="https://vuejs.org/">Vue.js</a>
            with
            <a href="https://firebase.google.com">Firebase</a>. -->
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
            to="/meetings"
            v-if="user"
          >Meetings</router-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'Home',
  components: {
  }
}
</script>

<style lang="scss">

</style>
