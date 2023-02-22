<template>
 <div class="flex h-screen"
 :style="{'background-image': 'url('+ bg + city +')'}">
  <div class="m-auto bg-white p-10 rounded-xl">
    <div class="flex items-center space-x-2">
      <input type="text" name="" id=""
      v-model="cityInput"
      @keypress.enter="getCity(cityInput)"
      class="border outline-none p-1 pl-3 rounded-full"
      placeholder="Search">
      <button class="border p-2 rounded-full" @click.prevent="getCity(cityInput)">
        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-search" viewBox="0 0 16 16">
          <path d="M11.742 10.344a6.5 6.5 0 1 0-1.397 1.398h-.001c.03.04.062.078.098.115l3.85 3.85a1 1 0 0 0 1.415-1.414l-3.85-3.85a1.007 1.007 0 0 0-.115-.1zM12 6.5a5.5 5.5 0 1 1-11 0 5.5 5.5 0 0 1 11 0z"/>
        </svg>
      </button>
    </div>
    <div class="my-4 space-y-4">
      <h1 class="text-3xl font-bold">Weather in {{ city }}</h1>
      <h2 class="text-4xl font-semibold">{{ temp }}°C</h2>
      <div>
        <p>{{ weather }}</p>
        <p><span class="font-semibold">Humidity:</span> {{ humidity }}%</p>
        <p><span class="font-semibold">Wind:</span> {{ wind }}km/h</p>
      </div>
    </div>
  </div>
</div>
</template>

<script setup>
import { ref } from 'vue'
import axios from 'axios'
import { capitalize } from "lodash"

const apiKey = ref('5fa61531f96af9f4761f5cc669bbf7ad')

const cityInput = ref(null)
const bg = ref('https://source.unsplash.com/1600x900/?')
const city = ref(null)
const temp = ref(null)
const weather = ref(null)
const humidity = ref(null)
const wind = ref(null)

async function getCity(city) {
  let api = await axios.get('https://api.openweathermap.org/data/2.5/weather?q=' + city + '&appid=' + apiKey.value)
  let data = api.data
  this.city = data.name
  this.temp = (data.main.temp - 273,15).toFixed(2)
  this.weather = capitalize(data.weather[0].description)
  this.humidity = data.main.humidity
  this.wind = data.wind.speed

}

</script>