<template>
  <div  class="register_form">
  <div class="container">
    <h1>Register</h1>
    <p>Please fill in this form to create an account.</p>
    <hr>
    <input type="text" placeholder="Enter First Name" name="firstName" id="firstName" required v-model="firstName">
    <br>
    <input type="text" placeholder="Enter Last Name" name="lastName" id="lastName" required v-model="lastName">
    <br>
    <input type="text" placeholder="Enter Phone Number" name="phoneNumber" id="phoneNumber" required v-model="phoneNumber">
    <br>
    <input type="password" placeholder="Enter Password" name="password" id="password" required v-model="password">
    <br>
    <input type="password" placeholder="Repeat Password" name="password2" id="password2" required v-model="password2">
    <hr>
    <p>By creating an account you agree to our <a href="#">Terms & Privacy</a>.</p>

    <button class="registerbtn" @click="register">Register</button>
  </div>
  
  <div class="container signin">
    <p>Already have an account? <a href="/login">Sign in</a>.</p>
  </div>
</div>
</template>

<style>

.register_form {
  max-width: 500px;
  margin: auto;
  padding: auto;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  background-color: black;
}

* {
  box-sizing: border-box;
}

/* Add padding to containers */
.container {
  padding: 16px;
  background-color: white;
  margin: auto;
  padding: auto;
}

/* Full-width input fields */
input[type=text], input[type=password] {
  width: 100%;
  padding: 15px;
  margin: 5px 0 22px 0;
  display: inline-block;
  border: none;
  background: #f1f1f1;
}

input[type=text]:focus, input[type=password]:focus {
  background-color: #ddd;
  outline: none;
}

/* Overwrite default styles of hr */
hr {
  border: 1px solid #f1f1f1;
  margin-bottom: 25px;
}

/* Set a style for the submit button */
.registerbtn {
  background-color: #04AA6D;
  color: white;
  padding: 16px 20px;
  margin: 8px 0;
  border: none;
  cursor: pointer;
  width: 100%;
  opacity: 0.9;
}

.registerbtn:hover {
  opacity: 1;
}

/* Add a blue text color to links */
a {
  color: dodgerblue;
}

/* Set a grey background color and center the text of the "sign in" section */
.signin {
  background-color: #f1f1f1;
  text-align: center;
}
</style>


<script>
// @ is an alias to /src
import Signup from '@/components/Signup.vue'

export default {
  name: 'SignupView',
  components: {
    Signup
  },
  data() {
    return {
      firstName: '',
      lastName: '',
      phoneNumber: '',
      password: '',
      password2: '',
    }
  },
  methods: {
    register () {
      console.log({hello: this.phoneNumber})
      fetch('http://localhost:8888/signup', {
          method: 'POST',
          headers: {
            'Accept': 'application/json',
            'Content-Type': 'application/json'
          },
          body: JSON.stringify({
              firstName: this.firstName, 
              lastName: this.lastName, 
              phoneNumber: this.phoneNumber, 
              password: this.password
            })
        })
        .then(res => res.json())
        .then(data => console.log('done'))
        .catch(err => console.log(err.message))
        .finally(() => {
          this.$router.push({path: '/login'});
        })   
    }
  }
}
</script>
