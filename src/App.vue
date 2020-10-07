<template>
  <div id="app">
    <Navigation
      :user="user"
      @logout="logout"
      :timestamp = timestamp
    />
    <router-view
      class="container"
      :user="user"
      :error="error"
      @logout="logout"
      :timestamp = timestamp
    />
  </div>
</template>

<script>
import Navigation from '@/components/Navigation.vue'
import Firebase from 'firebase'
import db from './db.js'

export default {
  name: 'App',
  data: function () {
    return {
      user: null,
      error: null,
      meetings: [],
      timestamp: ''
    }
  },
  created () {
    this.getNow()
    setInterval(this.getNow, 1000)
  },
  methods: {
    leadingZero (time) {
      if (time < 10) {
        return '0' + time
      }
      return time
    },
    getNow: function () {
      const monthNames = ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December']
      const dayNames = ['Saturday', 'Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
      const today = new Date()
      const date = dayNames[today.getDay()] + ' ' + monthNames[today.getMonth()] + ' ' + today.getDate() + ', ' + today.getFullYear()
      const time = this.leadingZero(today.getHours()) + ':' + this.leadingZero(today.getMinutes()) + ':' + this.leadingZero(today.getSeconds())
      const dateTime = date + ' ' + time
      this.timestamp = dateTime
    },
    logout: function () {
      Firebase.auth()
        .signOut()
        .then(() => {
          this.user = null
          this.$router.push('login')
        })
    }
    // addMeeting: function (payload) {
    //   db.collection('users')
    //     .doc(this.user.uid)
    //     .collection('meetings')
    //     .add({
    //       name: payload,
    //       createdAt: Firebase.firestore.FieldValue.serverTimestamp()
    //     })
    // },
    // deleteMeeting: function (payload) {
    //   db.collection('users')
    //     .doc(this.user.uid)
    //     .collection('meetings')
    //     .doc(payload)
    //     .delete()
    // },
    // checkIn: function (payload) {
    //   db.collection('users')
    //     .doc(payload.userID)
    //     .collection('meetings')
    //     .doc(payload.meetingID)
    //     .get()
    //     .then(doc => {
    //       if (doc.exists) {
    //         db.collection('users')
    //           .doc(payload.userID)
    //           .collection('meetings')
    //           .doc(payload.meetingID)
    //           .collection('attendees')
    //           .add({
    //             displayName: payload.displayName,
    //             eMail: payload.eMail,
    //             createdAt: Firebase.firestore.FieldValue.serverTimestamp()
    //           })
    //           .then(() =>
    //             this.$router.push(
    //               '/attendees/' + payload.userID + '/' + payload.meetingID
    //             )
    //           )
    //       } else {
    //         this.error = 'Sorry, no such meeting'
    //       }
    //     })
    // }
  },
  mounted () {
    Firebase.auth().onAuthStateChanged(user => {
      if (user) {
        this.user = user

        db.collection('')
          .doc(this.user.uid)
          .collection('')
          .onSnapshot(snapshot => {
            const snapData = []
            snapshot.forEach(doc => {
              snapData.push({
                id: doc.id,
                name: doc.data().name
              })
            })
            this.meetings = snapData.sort((a, b) => {
              if (a.name.toLowerCase() < b.name.toLowerCase()) {
                return -1
              } else {
                return 1
              }
            })
          })
      }
    })
  },
  components: {
    Navigation
  }
}
</script>

<style lang="scss">
body, html {
  height: 100%;
}

#app {
  /* The image used */
  // background-image: url("https://free4kwallpapers.com/uploads/originals/2015/05/21/chicago-at-night.jpg");

  /* Full height */
  height: 100%;

  /* Center and scale the image nicely */
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
}
// p {
//   color: rgb(226, 226, 226);
// }
// a:link {
//   color: rgb(226, 226, 226);
// }
$primary: #35383a;
@import "node_modules/bootstrap/scss/bootstrap";
</style>
