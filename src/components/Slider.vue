<template>
    <div class="slider">
      <transition-group
        tag="div"
        class="slider-inner"
        name="slider-transition"
        @before-enter="beforeEnter"
        @enter="enter"
        @after-enter="afterEnter"
        @before-leave="beforeLeave"
        @leave="leave"
        @after-leave="afterLeave"
      >
        <div v-for="slide in slides" :key="slide.id" class="slider-slide">
          <img :src="slide.imageUrl" :alt="slide.alt" />
        </div>
      </transition-group>
      <div class="slider-controls">
    <button @click="previousSlide">Previous</button>
    <button @click="nextSlide">Next</button>
  </div>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const slides = ref([
    { id: 1, imageUrl: 'path/to/slide1.jpg', alt: 'Slide 1' },
    { id: 2, imageUrl: 'path/to/slide2.jpg', alt: 'Slide 2' },
    { id: 3, imageUrl: 'path/to/slide3.jpg', alt: 'Slide 3' },
    // Add more slides as needed
  ]);
  
  // Slider logic and transition functions

let currentSlide = ref(0);

function nextSlide() {
  currentSlide.value = (currentSlide.value + 1) % slides.length;
}

function previousSlide() {
  currentSlide.value = (currentSlide.value - 1 + slides.length) % slides.length;
}

function beforeEnter(el) {
  el.style.opacity = 0;
}

function enter(el, done) {
  setTimeout(() => {
    el.style.opacity = 1;
    done();
  }, 50);
}

function afterEnter(el) {
  el.style.transition = '';
}

function beforeLeave(el) {
  el.style.transition = 'none';
}

function leave(el, done) {
  setTimeout(() => {
    el.style.opacity = 0;
    done();
  }, 50);
}

function afterLeave(el) {
  el.style.transition = '';
}

  </script>
  
  <style>
  /* Add your slider styles here */
  .slider {
    overflow: hidden;
  }
  
  .slider-inner {
    display: flex;
    transition: transform 0.3s ease-in-out;
  }
  
  .slider-slide {
    flex: 0 0 100%;
  }

  .slider-controls {
  display: flex;
  justify-content: center;
  margin-top: 20px;
}

.slider-controls button {
  margin: 0 5px;
}
  </style>
  