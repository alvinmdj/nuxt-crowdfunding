<template>
  <div class="container mx-auto h-screen flex justify-center items-center">
    <div class="w-full lg:w-1/3 px-10 lg:px-0">
      <div class="flex justify-center items-center mx-auto mb-4 w-40">
        <div class="relative">
          <div class="cursor-pointer" @click="$refs.file.click()">
            <img
              :src="url"
              alt=""
              class="rounded-full border-white border-4"
            />
            <img
              src="/icon-avatar-add.svg"
              alt=""
              class="absolute right-0 bottom-0 pb-2"
            />
            <input
              ref="file"
              type="file"
              style="display: none;"
              accept="image/*"
              @change="onFileChange"
            />
          </div>
        </div>
      </div>
      <h2 class="font-normal mb-3 text-3xl text-white text-center">
        Hi, {{ $store.state.auth.user.name }}
        <!-- same as : {{ $auth.user.name  }} -->
      </h2>
      <p class="text-white text-center font-light mb-4">
        Please upload your profile picture
      </p>
      <div class="mb-4 mt-6">
        <div class="mb-3">
          <button
            :disabled="typeof selectedFile === 'undefined'"
            :class="typeof selectedFile === 'undefined' ? 'opacity-50 cursor-not-allowed' : ''"
            class="block w-full bg-orange-button hover:bg-green-button text-white font-semibold px-6 py-4 text-lg rounded-full"
            @click="upload"
          >
            Sign Up Now
          </button>
        </div>
      </div>
      <div>
        <div class="mb-4">
          <button
            class="block w-full bg-transparent border-white border hover:bg-white hover:bg-opacity-25 text-white font-light px-6 py-4 text-lg rounded-full"
            @click="$router.push({ path: '/register-success' })"
          >
            Skip
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'UploadPage',
  layout: 'auth',
  data() {
    return {
      url: '/avatar.jpg',
      selectedFile: undefined,
    };
  },
  methods: {
    onFileChange(e) {
      const file = e.target.files[0];
      this.url = URL.createObjectURL(file);
      this.selectedFile = this.$refs.file.files;
    },
    async upload() {
      const formData = new FormData();
      formData.append('avatar', this.selectedFile.item(0));

      try {
        await this.$axios.post('/api/v1/avatars', formData, {
          headers: {
            'Content-Type': 'multipart/form-data',
          },
        });
        this.$toast.success('Avatar uploaded successfully');
        await this.$auth.fetchUser();
        this.$router.push({ path: '/register-success' });
      } catch (error) {
        this.$toast.error('Failed to upload avatar. Please try again.');
      }
    },
  },
}
</script>