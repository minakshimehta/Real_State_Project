<template>
    <swiper :slides-per-view="1" :space-between="10" navigation pagination>
      <swiper-slide v-for="layout in layouts" :key="layout.id">
        <div class="card">
          <h3>{{ layout.title }}</h3>
          <img :src="layout.url" :alt="layout.title" />
        </div>
      </swiper-slide>
    </swiper>
  </template>
  
  <script>
  import { Swiper, SwiperSlide } from 'swiper/vue';
  import 'swiper/swiper-bundle.css';
  
  export default {
    name: 'cardsCarousel',
    components: {
      Swiper,
      SwiperSlide
    },
    props: {
      layouts: {
        type: Array,
        required: true
      }
    }
  }
  </script>
  
  <style scoped>
  .card {
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
  }
  
  .card img {
    width: 100%;
    height: auto;
    border-radius: 8px;
  }
  
  .card h3 {
    margin-top: 10px;
    font-size: 1.2em;
    color: #333;
  }
  </style>
  