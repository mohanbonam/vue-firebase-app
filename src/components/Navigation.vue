<template>
  <div>
    <nav class="site-nav navbar navbar-expand bg-primary navbar-dark">
      <div class="container-fluid">
        <router-link class="navbar-brand" to="/"><i class="fas fa-magic fa-lg mr-2"></i>M O H A N B O N A M</router-link>
        <div class="navbar-nav ml-auto">
          <!-- <router-link
            class="nav-item nav-link"
            to="/secret"
            v-if="user"
          >secret content</router-link> -->
          <router-link
            class="nav-item nav-link"
            to="/login"
            v-if="!user"
          >log in</router-link>
          <router-link
            class="nav-item nav-link"
            to="/register"
            v-if="!user"
          >register</router-link>
          <button
            class="nav-item nav-link btn btn-link"
            @click="$emit('logout')"
            v-if="user"
          >
            logout
          </button>
        </div>
      </div>
    </nav>
  </div>
</template>
<script>
export default {
  name: 'navigation',
  props: ['user']
}
</script>
