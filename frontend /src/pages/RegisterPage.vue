<template>
  <div class="register">
    <h2>Register</h2>
    <form @submit.prevent="register">
      <input v-model="username" type="text" placeholder="Name" required />
      <input v-model="email" type="email" placeholder="Email" required />
      <input v-model="password" type="password" placeholder="Password" required />
      <button type="submit">Register</button>
      <p style="color: red">{{ error }}</p>
      <p style="color: green">{{ success }}</p>
    </form>
  </div>
</template>

<script>
import api from '../services/api'

export default {
  data() {
    return {
      username: '',
      email: '',
      password: '',
      
    }
  },
  methods: {
    async register() {
      try {
        await api.post('/auth/signup', {
          username: this.username,
          email: this.email,
          password: this.password,
        })
        this.success = 'Registration successful. Redirecting to login...'
        this.error = ''

        // Redirect to login after 2 seconds
        setTimeout(() => {
          this.$router.push('/dashboard')
        }, 2000)
      } catch (err) {
        this.error = err.response?.data?.message || 'Registration failed'
        this.success = ''
      }
    },
  },
}
</script>
