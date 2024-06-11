<template>
  <q-page class="flex flex-center">
    <div>
      <q-card>
        <q-card-section>
          <h2 class="text-center">Cuaca</h2>
        </q-card-section>
        <q-card-section>
          <q-input v-model="city" label="Masukkan kota" />
          <!-- Menambahkan kelas 'bg-black' untuk tombol -->
          <q-btn class="bg-black" label="Cari" @click="fetchWeather" color="primary" />
        </q-card-section>
        <q-card-section v-if="weather">
          <h3>Lokasi: {{ weather.name }}</h3>
          <p class="text-red-5">Temperatur: {{ weather.main.temp }}°C</p>
          <p>Deskripsi: {{ weather.weather[0].description }}</p>
        </q-card-section>
        <q-card-section v-if="error">
          <p class="text-red-5">{{ error }}</p>
        </q-card-section>
      </q-card>
    </div>
  </q-page>
</template>

<script>
import axios from 'axios'

export default {
  name: 'WeatherPage',
  data() {
    return {
      city: '',
      weather: null,
      error: ''
    }
  },
  methods: {
    async fetchWeather() {
      const apiKey = '94bf6d59f86ae95e8071e78240546056'
      const url = `https://api.openweathermap.org/data/2.5/weather?q=${this.city}&units=metric&appid=${apiKey}`
      try {
        const response = await axios.get(url)
        this.weather = response.data
        this.error = '' // Reset error message if successful
        console.log(this.weather) // Debugging output
      } catch (error) {
        this.error = 'Kota tidak ditemukan' // Set error message
        console.error(error)
      }
    }
  }
}
</script>

<style scoped>
.text-red-5 {
  color: #f44336;
}

/* Menentukan warna tombol 'Cari' menjadi hitam */
.bg-black {
  background-color: #000000;
  color: #ffffff; /* Mengatur warna teks menjadi putih */
}
</style>
