<template>
  <div class='h-screen flex justify-center items-center'>
    <div
      class='hidden md:block lg:w-1/3 bg-white h-full auth-background rounded-tr-lg rounded-br-lg'
    ></div>
    <div class='w-auto md:w-2/4 lg:w-2/3 flex justify-center items-center'>
      <div class='w-full lg:w-1/2 px-10 lg:px-0'>
        <h2 class='font-normal mb-6 text-3xl text-white'>
          Sign In to Your Account
        </h2>
        <DangerAlert v-if="errorMessage !== ''" :error-message="errorMessage" />
        <div class='my-6'>
          <div class='mb-4'>
            <label class='font-normal text-lg text-white block mb-3'>
              Email Address
            </label>
            <input
              v-model='login.email'
              type='email'
              class='auth-form focus:outline-none focus:bg-purple-hover focus:shadow-outline focus:border-purple-hover-stroke focus:text-gray-100'
              placeholder='Email address'
            />
          </div>
        </div>
        <div class='mb-6'>
          <div class='mb-4'>
            <label class='font-normal text-lg text-white block mb-3'>
              Password
            </label>
            <input
              v-model='login.password'
              type='password'
              class='auth-form focus:outline-none focus:bg-purple-hover focus:shadow-outline focus:border-purple-hover-stroke focus:text-gray-100'
              placeholder='Password'
              @keyup.enter='userLogin'
            />
          </div>
        </div>
        <div class='mb-6'>
          <div class='mb-4'>
            <button
              class='block w-full bg-orange-button hover:bg-green-button text-white font-semibold px-6 py-4 text-lg rounded-full'
              @click='userLogin'
            >
              Sign In
            </button>
          </div>
        </div>
        <div class='text-center'>
          <p class='text-white text-md'>
            Don't have account?
            <NuxtLink to='/register' class='no-underline text-orange-button'>
              Sign Up
            </NuxtLink>
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import DangerAlert from '~/components/DangerAlert.vue';

export default {
  name: 'LoginPage',
  components: { DangerAlert },
  layout: 'auth',
  data() {
    return {
      login: {
        email: '',
        password: '',
      },
      errorMessage: '',
    };
  },
  methods: {
    async userLogin() {
      try {
        // Check if all fields are filled
        if (!this.login.email || !this.login.password) {
          this.errorMessage = 'Please fill in all fields';
          return;
        }

        // call the login endpoint set in nuxt.config.js
        const response = await this.$auth.loginWith('local', { data: this.login });
        this.$auth.setUser(response.data.data);
      }
      catch (error) {
        if (error.response.status === 422) {
          this.errorMessage = 'Email or password is incorrect.';
        } else {
          this.errorMessage = 'An unknown error occurred. Please try again.';
        }
      }
    },
  },
}
</script>

<style scoped>
.auth-background {
  background-image: url('/sign-in-background.jpg');
  background-position: center;
  background-size: cover;
}
</style>