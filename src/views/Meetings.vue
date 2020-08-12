<template>
  <div class="container mt-4">
    <div class="row justify-content-center">
      <div class="col-12 col-md-9 col-lg-7">
        <div class="text-secondary text-center">
          <div
            v-if="user"
            class="text-center"
          >
            Welcome <br>
            <span class="font-weight-bold text-info">{{user.displayName}}</span>
            <h4 class="display-5 text-primary mb-2">You are being watched</h4>
            <a
              href="#"
              role="button"
              class="text-primary"
              @click="$emit('logout')"
            >logout</a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'meetings',
  data: function () {
    return {
    }
  },
  methods: {
    // handleAdd: function() {
    //   this.$emit("addMeeting", this.meetingName);
    //   this.meetingName = null;
    //   this.$refs.meetingName.focus();
    // }
  },
  props: ['user']
}
</script>
