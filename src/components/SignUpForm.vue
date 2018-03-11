<template>
  <form
    class="login"
    @submit.prevent="onSubmit">
    <fieldset>
      <legend>
        <h2>Sign Up</h2>
      </legend>
      <div>
        <input
          v-model="email"
          type="text"
          placeholder="Email">
      </div>
      <div>
        <input
          v-model="password"
          type="password"
          placeholder="Password">
      </div>
    </fieldset>
    <button type="submit">Sign up</button>
    <p>
      <router-link to="/login">Sign in</router-link>
    </p>
  </form>
</template>
<script>
import firebase from 'firebase'

export default {
  name: 'SignupForm',
  data () {
    return {
      email: '',
      password: ''
    }
  },
  methods: {
    onSubmit () {
      firebase.auth().createUserWithEmailAndPassword(this.email, this.password).then((user) => {
        this.$router.replace('login')
      }, (err) => {
        alert('Opps. ' + err.message)
      })
    }
  }
}
</script>
