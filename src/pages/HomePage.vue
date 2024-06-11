<template>
  <q-page class="flex flex-center">
    <div>
      <h1>Weather Widget by HAN</h1>
      <q-btn label="Go to Weather" @click="goToWeather" color="primary" />
    </div>
  </q-page>
</template>

<script>
export default {
  name: 'HomePage',
  methods: {
    goToWeather() {
      this.$router.push('/weather')
    }
  }
}
</script>
