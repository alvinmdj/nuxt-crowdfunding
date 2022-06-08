<template>
  <div class="h-screen flex justify-center items-center">
    <div
      class="hidden md:block lg:w-1/3 bg-white h-full auth-background rounded-tr-lg rounded-br-lg"
    ></div>
    <div class="w-auto md:w-2/4 lg:w-2/3 flex justify-center items-center">
      <div class="w-full lg:w-1/2 px-10 lg:px-0">
        <h2 class="font-normal mb-6 text-3xl text-white">
          Sign Up Account
        </h2>
        <DangerAlert v-if="errorMessage" :error-message="errorMessage" />
        <div class="mb-6 mt-3">
          <div class="mb-4">
            <label class="font-normal text-lg text-white block mb-3">
              Full Name
            </label>
            <input
              v-model="register.name"
              type="text"
              class="auth-form focus:outline-none focus:bg-purple-hover focus:shadow-outline focus:border-purple-hover-stroke focus:text-gray-100"
              placeholder="Write Your Name Here"
            />
          </div>
        </div>
        <div class="mb-6">
          <div class="mb-4">
            <label class="font-normal text-lg text-white block mb-3">
              Occupation
            </label>
            <input
              v-model="register.occupation"
              type="text"
              class="auth-form focus:outline-none focus:bg-purple-hover focus:shadow-outline focus:border-purple-hover-stroke focus:text-gray-100"
              placeholder="Write your occupation here"
            />
          </div>
        </div>
        <div class="mb-6">
          <div class="mb-4">
            <label class="font-normal text-lg text-white block mb-3">
              Email Address
            </label>
            <input
              v-model="register.email"
              type="email"
              class="auth-form focus:outline-none focus:bg-purple-hover focus:shadow-outline focus:border-purple-hover-stroke focus:text-gray-100"
              placeholder="Write your email address here"
            />
          </div>
        </div>
        <div class="mb-6">
          <div class="mb-4">
            <label class="font-normal text-lg text-white block mb-3">
              Password
            </label>
            <input
              v-model="register.password"
              type="password"
              class="auth-form focus:outline-none focus:bg-purple-hover focus:shadow-outline focus:border-purple-hover-stroke focus:text-gray-100"
              placeholder="Type your password here"
              @keyup.enter="userRegister"
            />
          </div>
        </div>
        <div class="mb-6">
          <div class="mb-4">
            <button
              class="block w-full bg-orange-button hover:bg-green-button text-white font-semibold px-6 py-4 text-lg rounded-full"
              @click="userRegister"
            >
              Sign Up
            </button>
          </div>
        </div>
        <div class="text-center">
          <p class="text-white text-md">
            Already have account?
            <NuxtLink to="/login" class="no-underline text-orange-button">
              Sign In
            </NuxtLink>
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "RegisterPage",
  layout: "auth",
  data() {
    return {
      register: {
        name: '',
        occupation: '',
        email: '',
        password: '',
      },
      errorMessage: '',
    }
  },
  methods: {
    async userRegister() {
      try {
        // Check if all fields are filled
        if (!this.register.name || !this.register.occupation || !this.register.email || !this.register.password) {
          this.errorMessage = 'Please fill all the fields';
          return;
        }

        // Check if email is already registered
        const { data } = await this.$axios.$post('/api/v1/email_checkers', {
          email: this.register.email,
        });
        if (!data.is_available) {
          this.errorMessage = 'Email already exists';
          return;
        }

        // Register user
        const response = await this.$axios.$post('/api/v1/users', this.register);
        this.$auth.setUserToken(response.data.token)
          .then(() => this.$router.push({ path: '/upload' }));
      } catch (error) {
        this.errorMessage = 'An unknown error occurred. Please try again.';
      }
    },
  },
}
</script>

<style scoped>
.auth-background {
  background-image: url("/sign-up-background.jpg");
  background-position: center;
  background-size: cover;
}
</style>