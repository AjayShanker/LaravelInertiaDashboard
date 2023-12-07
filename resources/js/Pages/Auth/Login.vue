<template>
  <Head title="Login" />
  <div class="flex items-center justify-center p-6 min-h-screen " style="background: #020917;">
    <div class="flex flex-col md:flex-row">
      <div class="h-32 md:h-auto md:w-1/3 h-screen"
        style="background-image: url('/images/log-in-girl.svg');background-size: contain;background-repeat: no-repeat;width: 100%; height: 660px; margin-top: 12%;">
        <img class="object-cover w-full h-full" src="/images/log-in-girl.svg" alt="img"
          style="border-style: none; background: radial-gradient(circle, #202047 0, #020917 100%); visibility: hidden;" />
      </div>
      <div class="flex items-center justify-center p-6 sm:p-12 md:w-2/3">
        <div class="w-full  h-full">
          <logo class="block mx-auto w-full max-w-xs fill-white" height="50" />
          <form class="mt-8 bg-white rounded-lg shadow-xl overflow-hidden" @submit.prevent="login">
            <div class="px-10 py-12">
              <h1 class="text-center text-3xl font-bold">Welcome Back!</h1>
              <div class="mt-6 mx-auto w-24 border-b-2" />
              <text-input v-model="form.email" :error="form.errors.email" class="mt-10" label="Email" type="email"
                autofocus autocapitalize="off" />
              <text-input v-model="form.password" :error="form.errors.password" class="mt-6" label="Password"
                type="password" />
              <label class="flex items-center mt-6 select-none" for="remember">
                <input id="remember" v-model="form.remember" class="mr-1" type="checkbox" />
                <span class="text-sm">Remember Me</span>
              </label>
            </div>
            <div class="flex px-10 py-4 bg-gray-100 border-t border-gray-100">
              <loading-button :loading="form.processing" class="btn-indigo ml-auto" type="submit"
                style="background-color: #166bff;">Login</loading-button>
            </div>            
          </form>
          <hr class="my-8" />


            <div class="flex items-center justify-center gap-4 px-5 py-4">
              <a class="flex items-center justify-center w-full px-4 py-2 text-sm text-white text-gray-700 border border-gray-300 rounded-lg hover:border-gray-500 focus:border-gray-500"
                href="javascript:void(0)" style="background: white;">
                <svg class="w-4 h-4 mr-2" aria-hidden="true" viewBox="0 0 24 24" fill="currentColor">
                  <path
                    d="M12 .297c-6.63 0-12 5.373-12 12 0 5.303 3.438 9.8 8.205 11.385.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61C4.422 18.07 3.633 17.7 3.633 17.7c-1.087-.744.084-.729.084-.729 1.205.084 1.838 1.236 1.838 1.236 1.07 1.835 2.809 1.305 3.495.998.108-.776.417-1.305.76-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.465-2.38 1.235-3.22-.135-.303-.54-1.523.105-3.176 0 0 1.005-.322 3.3 1.23.96-.267 1.98-.399 3-.405 1.02.006 2.04.138 3 .405 2.28-1.552 3.285-1.23 3.285-1.23.645 1.653.24 2.873.12 3.176.765.84 1.23 1.91 1.23 3.22 0 4.61-2.805 5.625-5.475 5.92.42.36.81 1.096.81 2.22 0 1.606-.015 2.896-.015 3.286 0 .315.21.69.825.57C20.565 22.092 24 17.592 24 12.297c0-6.627-5.373-12-12-12" />
                </svg>
                Github
              </a>
              <a class="flex items-center justify-center w-full px-4 py-2 text-sm text-white text-gray-700 border border-gray-300 rounded-lg hover:border-gray-500 focus:border-gray-500"
                href="javascript:void(0)" style="background: white;">
                <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" class="w-4 h-4 mr-2"
                  viewBox="0 0 48 48">
                  <defs>
                    <path id="a"
                      d="M44.5 20H24v8.5h11.8C34.7 33.9 30.1 37 24 37c-7.2 0-13-5.8-13-13s5.8-13 13-13c3.1 0 5.9 1.1 8.1 2.9l6.4-6.4C34.6 4.1 29.6 2 24 2 11.8 2 2 11.8 2 24s9.8 22 22 22c11 0 21-8 21-22 0-1.3-.2-2.7-.5-4z" />
                  </defs>
                  <clipPath id="b">
                    <use xlink:href="#a" overflow="visible" />
                  </clipPath>
                  <path clip-path="url(#b)" fill="#FBBC05" d="M0 37V11l17 13z" />
                  <path clip-path="url(#b)" fill="#EA4335" d="M0 11l17 13 7-6.1L48 14V0H0z" />
                  <path clip-path="url(#b)" fill="#34A853" d="M0 37l30-23 7.9 1L48 0v48H0z" />
                  <path clip-path="url(#b)" fill="#4285F4" d="M48 48L17 24l-4-3 35-10z" />
                </svg>Google
              </a>
            </div>
        </div>
      </div>
    </div>

  </div>
</template>

<script>
import { Head } from '@inertiajs/inertia-vue3'
import Logo from '@/Shared/Logo'
import TextInput from '@/Shared/TextInput'
import LoadingButton from '@/Shared/LoadingButton'

export default {
  components: {
    Head,
    LoadingButton,
    Logo,
    TextInput,
  },
  data() {
    return {
      form: this.$inertia.form({
        email: 'ajay@example.com',
        password: 'secret',
        remember: false,
      }),
    }
  },
  methods: {
    login() {
      this.form.post('/login')
    },
  },
}
</script>
