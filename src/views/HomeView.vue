<template>
  <div class="home">
    <div class="content">
      <Carousel
       :navigation="true"
       :pagination="false" 
       :startAutoPlay="true"
       :timeOut="5000"
       class="carousel" 
       v-slot="{ currentSlide }"
      >
        <Slide v-for="(slide, index) in carouselSlides" :key="index">
          <div v-show="currentSlide === index +1" class="slide-info">
            <img :src="require(`../assets/${slide}.jpg`)" alt="#" />
          </div>
        </Slide>
      </Carousel>
    </div>
  </div>
</template>

<script>
  import Carousel from '@/components/CarouselComp.vue';
  import Slide from '@/components/SlideComp.vue';

  export default {
    name: 'HomeView',
    components: {
      Carousel, Slide
    },
    setup() {
      const carouselSlides = ["bg-1", "bg-2", "bg-3", "bg-4", "bg-5"];
      return { carouselSlides };
    }  
  }
</script>

<style lang="scss" scoped>
  .carousel {
    position: relative;
    max-height: 100vh;
    height: 100vh;

    .slide-info {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      max-height: 100%;
      height: 100%;

      img {
        min-width: 100%;
        height: 100%;
        object-fit: cover;
      }
    }
  }    
      
</style>