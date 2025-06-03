<template>
  <div class="auth-container min-h-screen bg-gradient-to-br from-gray-100 to-blue-200 flex flex-col items-center justify-center px-4">
    <h1 class="text-3xl sm:text-4xl font-bold text-gray-800 mb-8 text-center drop-shadow-md">
      ⚡ EV Charging Station System
    </h1>

    <!-- Show buttons initially -->
    <div v-if="!showForm" class="space-x-4">
      <button
        @click="showForm = 'login'"
        class="px-6 py-3 bg-blue-600 text-white rounded-lg shadow hover:bg-blue-700 transition"
      >
        Login
      </button>
      <button
        @click="showForm = 'register'"
        class="px-6 py-3 bg-green-600 text-white rounded-lg shadow hover:bg-green-700 transition"
      >
        Register
      </button>
    </div>

    <!-- Show Login form -->
    <div v-if="showForm === 'login'" class="w-full max-w-md mt-8">
      <LoginPage @back="showForm = null" />
    </div>

    <!-- Show Register form -->
    <div v-if="showForm === 'register'" class="w-full max-w-md mt-8">
      <RegisterPage @back="showForm = null" />
    </div>
  </div>
</template>

<script>
import LoginPage from './LoginPage.vue'
import RegisterPage from './RegisterPage.vue'

export default {
  components: { LoginPage, RegisterPage },
  data() {
    return {
      showForm: null,
    }
  },
}
</script>
