<template>
  <div>
    <CarouselComponent class="carousel" :navigation="false" :pagination="false" :start-auto-play="true" :time-out="2000"
      v-slot="{ currentSlide }">
      <SlideCarousel v-show="currentSlide === index + 1" v-for="(slide, index) in carouselSlides" :key="index">
        <div class="slide-info">
          <img v-if="imagePaths[slide]" :src="imagePaths[slide]" alt="">
          <p v-else>Loading...</p>
        </div>
      </SlideCarousel>
    </CarouselComponent>

    <section class="featured-section">
      <div class="latest-products">
        <CardLatestComponent v-for="item in latestProducts" :key="item.id" :item="item" />
      </div>
    </section>

    <section class="featured-section">
      <div class="section-title">
        <p class="text-title"><a>Home</a>/<span>All</span></p>
      </div>
      <div class="grid-view">
        <CardComponent v-for="item in dataProduct" :key="item.id" :item="item" />
      </div>
    </section>
  </div>
</template>

<script setup>
import axios from 'axios';
import { ref, onMounted } from 'vue';
import CardComponent from '@/components/CardComponent.vue';
import CardLatestComponent from '@/components/CardLatestComponent.vue';
import CarouselComponent from '@/components/CarouselComponent.vue';
import SlideCarousel from '@/components/SlideCarousel.vue';
import { apiUrl } from '@/api/apiUrl';

const latestProducts = ref([]);
const dataProduct = ref([]);
const carouselSlides = ['banner-1', 'banner-2', 'banner-3'];

const imagePaths = ref({});

const getImagePath = async (slide) => {
  try {
    const imagePath = await import(`@/assets/img/${slide}.jpg`);
    imagePaths.value = { ...imagePaths.value, [slide]: imagePath.default };
  } catch (error) {
    console.error('Error importing image:', error);
    imagePaths.value = { ...imagePaths.value, [slide]: '' };
  }
};

onMounted(async () => {
  try {
    const apiProduct = apiUrl.product;
    const response = await axios.get(apiProduct);

    latestProducts.value = response.data.aaData.slice(0, 3);
    dataProduct.value = response.data.aaData;
    console.log(dataProduct.value);

    await Promise.all(carouselSlides.map(async (slide) => {
      await getImagePath(slide);
    }));
  } catch (error) {
    console.error('Error fetching product data:', error);
  }
});
</script>
<style scoped>

.carousel {
  margin-top: 2rem;
  position: relative;
  max-height: 100vh;
  height: 70vh;
  overflow: hidden;

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

.section-title {
  width: 100%;
  background-color: #333; 
  padding: 10px; 
  text-align: left;
  color: #fff;
  border-bottom: 2px solid #555;

  .text-title {
    margin: 0;
    font-size: 12px; 
  }
}

.featured-section {
  margin-top: 40px;
}

.latest-products{
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
}

 .grid-view {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 16px;
  justify-content: center;
}
</style>
