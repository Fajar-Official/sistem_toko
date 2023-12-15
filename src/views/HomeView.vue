<template>
  <div>
    <!-- <CarouselComponent /> -->

    <section class="featured-section">
      <h2 class="section-title">Produk Terbaru</h2>
      <div class="latest-products">
        <CardComponent v-for="product in latestProducts" :key="product.id" :item="product" />
      </div>
    </section>

    <section class="featured-section">
      <h2 class="section-title">Grid View</h2>
      <div class="grid-view">
        <CardComponent v-for="item in gridItems" :key="item.id" :item="item" />
      </div>
    </section>
  </div>
</template>

<script setup>
import axios from 'axios';
import { ref, onMounted } from 'vue';
// import CarouselComponent from '@/components/CarouselComponent.vue';
import CardComponent from '@/components/CardComponent.vue';

const latestProducts = ref([]);
const gridItems = ref([]);

onMounted(async () => {
  try {
    const apiProduct = 'https://sistemtoko.com/public/demo/product';
    const response = await axios.get(apiProduct);
    latestProducts.value = response.data.aaData.slice(0, 3);
    gridItems.value = response.data.aaData;
  } catch (error) {
    console.error('Error fetching product data:', error);
  }
});
</script>

<style scoped>
/* Your existing styles here */
</style>


<style scoped>
.section-title {
  text-align: center;
  margin-top: 24px;
  font-size: 1.5rem;
}

.featured-section {
  margin-top: 40px;
}

.latest-products,
.grid-view {
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
