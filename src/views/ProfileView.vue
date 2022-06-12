<template>
    <br>
    <br>
    <br>
    <br>
  <div  class="profile">
  <div class="container">
    <h1>Profile</h1>
    <p>Below is your profile information</p>
    <hr>
    <b>First Name</b> : {{ firstName }}
    <br>
    <b>Last Name</b> : {{ lastName }}
    <br>
    <b>Phone Number</b> : {{ phoneNumber }}
    <br>
    <b>Created At</b> : {{ createdAt }}
    <br>
    <br>
    <br>
    <br>
    <br>
    <br>

    <button class="registerbtn" @click="logout">Logout</button>
  </div>
</div>
</template>

<style>
  
.profile {
  max-width: 800px;
  margin: auto;
  padding: auto;
}
</style>

<script>
// @ is an alias to /src
import Profile from '@/components/Profile.vue'

export default {
  name: 'ProfileView',
  components: {
    Profile
  },
  data() {
    return {
      firstName: 'Marvin',
      lastName: 'Sendikaddiwa',
      phoneNumber: '256702544870',
      createdAt: '2022-06-12',
    }
  },
  methods: {
    logout () {
      // console.log({hello: this.phoneNumber})
      this.$router.push({path: '/login'});  
    }
  }
}
</script>
