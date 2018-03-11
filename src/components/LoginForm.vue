<template>
  <form
    class="login"
    @submit.prevent="onSubmit">
    <fieldset>
      <legend>
        <h2>Sign In</h2>
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
    <button type="submit">Login</button>
    <p>
      <router-link to="/signup">Sign up</router-link>
    </p>
  </form>
</template>
<script>
import firebase from 'firebase'

export default {
  name: 'LoginForm',
  data () {
    return {
      email: '',
      password: ''
    }
  },
  methods: {
    onSubmit () {
      firebase.auth().signInWithEmailAndPassword(this.email, this.password).then((user) => {
        this.$router.replace('hello')
      }, (err) => {
        alert(err.message)
      })
    }
  }
}
</script>
