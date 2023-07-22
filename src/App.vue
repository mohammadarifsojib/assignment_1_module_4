<script setup>
import {ref} from "vue";

const sliders = ref([
  {
    name: 'Red car',
    path: 'https://images.unsplash.com/photo-1682685797769-481b48222adf?ixlib=rb-4.0.3&ixid=M3wxMjA3fDF8MHxlZGl0b3JpYWwtZmVlZHwxfHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60',
  },
  {
    name: 'White car',
    path: 'https://images.unsplash.com/photo-1682695794816-7b9da18ed470?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDZ8fHxlbnwwfHx8fHw%3D&auto=format&fit=crop&w=1024&q=60',
  },
  {
    name: 'Blue car',
    path: 'https://images.unsplash.com/photo-1682685797661-9e0c87f59c60?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE4fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60',
  },
  {
    name: 'Blue car',
    path: 'https://plus.unsplash.com/premium_photo-1666963323736-5ee1c16ef19d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60',
  },
])

const sliderIndex = ref(0)

function prevSlider() {
  if (sliderIndex.value) {
    sliderIndex.value--
  } else {
    sliderIndex.value = sliders.value.length - 1
  }
}

function nextSlider() {
  if (sliderIndex.value < sliders.value.length - 1) {
    sliderIndex.value++
  } else {
    sliderIndex.value = 0
  }
}
</script>

<template>
  <main class="min-h-screen w-full py-20 px-5 flex items-center justify-center bg-gray-200">
    <!-- Slider wrapper -->
    <div class="w-full relative">

      <!-- Single Slider -->
      <div v-show="sliderIndex === index" v-for="(slider,index) in sliders"
           :key="index">
        <img :src="slider.path" alt="car"
             class="w-full h-96 object-cover rounded-lg shadow">
        <p class="text-center mt-3 text-gray-200 text-xl uppercase">
          {{ slider.name }}
        </p>
      </div>
      <!-- Single Slider end -->

      <!-- Arrows prev -->
      <button @click="prevSlider"
              class="w-10 h-10 rounded-full bg-white hover:shadow-lg active:scale-90 transition absolute left-2 top-40 text-gray-700 flex items-center justify-center opacity-50 hover:opacity-100">
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor"
             class="w-6 h-6">
          <path stroke-linecap="round" stroke-linejoin="round" d="M15.75 19.5L8.25 12l7.5-7.5"/>
        </svg>
      </button>
      <!-- Arrows prev end -->

      <!-- Arrows next -->
      <button @click="nextSlider"
              class="w-10 h-10 rounded-full bg-white hover:shadow-lg active:scale-90 transition absolute right-2 top-40 text-gray-700 flex items-center justify-center opacity-50 hover:opacity-100">
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor"
             class="w-6 h-6">
          <path stroke-linecap="round" stroke-linejoin="round" d="M8.25 4.5l7.5 7.5-7.5 7.5"/>
        </svg>
      </button>
      <!-- Arrows next end -->

    </div>
  </main>
</template>