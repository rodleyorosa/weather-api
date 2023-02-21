<template>
 <div class="flex h-screen bg-gray-100">
  <div class="m-auto bg-white p-10 rounded-xl">
    <div class="flex items-center space-x-2">
      <input type="text" name="" id=""
      class="border outline-none p-1 pl-3 rounded-full"
      placeholder="Search">
      <button class="border p-2 rounded-full">
        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-search" viewBox="0 0 16 16">
          <path d="M11.742 10.344a6.5 6.5 0 1 0-1.397 1.398h-.001c.03.04.062.078.098.115l3.85 3.85a1 1 0 0 0 1.415-1.414l-3.85-3.85a1.007 1.007 0 0 0-.115-.1zM12 6.5a5.5 5.5 0 1 1-11 0 5.5 5.5 0 0 1 11 0z"/>
        </svg>
      </button>
    </div>
    <div class="my-4 space-y-4">
      <h1 class="text-3xl font-bold">Weather in Tokyo</h1>
      <h2 class="text-4xl font-semibold">9°C</h2>
      <div>
        <p>Broken clouds</p>
        <p><span class="font-semibold">Humidity:</span> 66%</p>
        <p><span class="font-semibold">Wind:</span> 3.6km/h</p>
      </div>
    </div>
  </div>
</div>
</template>

<script setup>
import { ref } from 'vue'

const apiKey = ref('5fa61531f96af9f4761f5cc669bbf7ad')
const api = ref('https://api.openweathermap.org/data/2.5/weather?q={city name}&appid={API key}')

</script>