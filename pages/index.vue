<template>
  <div class="container">
    <div>
      <logo />
      <h1 class="title">
        reCAPTCHA v3
      </h1>
      <h2 class="subtitle">
        My prime Nuxt.js project
      </h2>
      <div class="links">
        <nuxt-link to="/recaptcha" class="button--green">
          reCAPTCHA v2
        </nuxt-link>
        <button class="button--grey" @click="recaptcha">
          Execute recaptcha
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import Vue from 'vue'
import { VueReCaptcha } from 'vue-recaptcha-v3'
import Logo from '~/components/Logo.vue'

// For more options see below
Vue.use(VueReCaptcha, { siteKey: '<site key>' })

export default {
  components: {
    Logo
  },
  methods: {
    async recaptcha() {
      // (optional) Wait until recaptcha has been loaded.
      await this.$recaptchaLoaded()

      // Execute reCAPTCHA with action "login".
      const token = await this.$recaptcha('login')

      // Do stuff with the received token.
      // eslint-disable-next-line no-console
      console.log(token)
    }
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
