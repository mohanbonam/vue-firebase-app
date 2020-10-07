<template>
  <div class="container mt-4">
    <div class="row justify-content-center">
      <div class="col-12 col-md-9 col-lg-7">
        <div class="text-secondary text-center">
          <div v-if="user">
            <p>Welcome <br><span class="font-weight-bold text-info">{{user.displayName}}</span></p>
            <p>You are being watched</p>
            <p>User id <pre>{{user.uid}}</pre> </p>
            <!-- <p>your password{{user.email}} </p> -->
            <!-- <p>your password{{user.password}} </p> -->
            <a
              href="#"
              role="button"
              class="text-primary"
              @click="$emit('logout')"
            >logout</a>
          </div>
          <hr>
          <button class="btn btn-secondary" @click="printthis">print</button>
          <small>{{timestamp}}</small><br>
          <button class="btn btn-primary"  @click="startTimer">start timer</button>
          <div class="meta">
            <section id="clock">
              <div class="timer">{{timer}}</div>
              <button id="reset" class="btn btn-primary" @click="resetTimer">Reset</button>
            </section>
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
      timer: '00:00:00',
      arrTimer: [0, 0, 0, 0]
    }
  },
  methods: {
    // handleAdd: function() {
    //   this.$emit("addMeeting", this.meetingName);
    //   this.meetingName = null;
    //   this.$refs.meetingName.focus();
    // }
    startTimer () {
      setInterval(this.runTimer, 10)
    },
    leadingZero (time) {
      if (time < 10) {
        return '0' + time
      }
      return time
    },
    runTimer () {
      const arr = this.arrTimer
      var currentTime = this.leadingZero(arr[0]) + ':' + this.leadingZero(arr[1]) + ':' + this.leadingZero(arr[2])
      this.timer = currentTime
      arr[3]++
      arr[0] = Math.floor((arr[3] / 100) / 60)
      arr[1] = Math.floor((arr[3] / 100) - (arr[0] * 60))
      arr[2] = Math.floor(arr[3] - (arr[1] * 100) - (arr[0] * 6000))
      console.log(this.timer)
    },
    // reset everthing
    resetTimer () {
      console.log('reset button has been pressed')
    },
    printthis () {
      window.print()
    }
  },
  props: ['user', 'timestamp']
}
</script>
