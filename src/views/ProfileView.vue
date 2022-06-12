<template>
  <div class="Profile">
    <!-- <img alt="Vue logo" src="../assets/logo.png"> -->
    <Profile msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import Profile from '@/components/Profile.vue'

export default {
  name: 'ProfileView',
  components: {
    Profile
  }
}
</script>
