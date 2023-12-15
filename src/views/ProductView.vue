<template>
    <div>
        <section class="featured-section">
            <h2 class="section-title">Grid View</h2>
            <div class="grid-view">
                <CardComponent v-for="item in gridItems" :key="item.id" :item="item" @click="showModal(item.id)" />
            </div>
        </section>

        <!-- Tambahkan modal di sini -->
        <ProductDetail :productId="selectedProductId" v-if="isModalVisible" @closeModal="closeModal" />
    </div>
</template>

<script setup>
import axios from 'axios';
import { ref, onMounted } from 'vue';
import CardComponent from '@/components/CardComponent.vue';
import ProductDetail from '@/views/ProductDetail.vue'; // Sesuaikan dengan nama komponen modal Anda

const gridItems = ref([]);
const isModalVisible = ref(false);
const selectedProductId = ref(null);

onMounted(async () => {
    try {
        const apiProduct = 'https://sistemtoko.com/public/demo/product';
        const response = await axios.get(apiProduct);
        gridItems.value = response.data.aaData;
    } catch (error) {
        console.error('Error fetching product data:', error);
    }
});

const showModal = (productId) => {
    selectedProductId.value = productId;
    isModalVisible.value = true;
};

const closeModal = () => {
    isModalVisible.value = false;
};
</script>

<style scoped>
.section-title {
    text-align: center;
    margin-top: 24px;
    font-size: 1.5rem;
}

.featured-section {
    margin-top: 40px;
}

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
