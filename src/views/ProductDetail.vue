<template>
    <div class="modal" @click="$router.push('/')">
        <div class="modal-content" @click.stop>
            <span class="close" @click="$router.push('/')">&times;</span>
            <h1>{{ product.product_name }}</h1>
            <img :src="getProductImage" alt="Product Image" />
            <p>{{ product.product_description }}</p>
            <p>Price: {{ formatCurrency(product.product_price) }}</p>
        </div>
    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';
import { useRouter } from 'vue-router';

const product = ref({});
const router = useRouter();

onMounted(async () => {
    const productId = router.params.id;
    await fetchData(productId);
});

const fetchData = async (productId) => {
    try {
        const response = await axios.get(`https://sistemtoko.com/public/demo/single/${productId}`);
        product.value = response.data;
    } catch (error) {
        console.error('Error fetching product data:', error);
    }
};

const getProductImage = () => {
    return `https://sistemtoko.com/img/user/demo/product/${product.value.product_img}`;
};

const formatCurrency = (price) => {
    return new Intl.NumberFormat('id-ID', { style: 'currency', currency: 'IDR' }).format(price);
};
</script>

<style scoped>
.modal {
    display: flex;
    justify-content: center;
    align-items: center;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
}

.modal-content {
    background-color: #fff;
    padding: 20px;
    border-radius: 8px;
    position: relative;
}

.close {
    position: absolute;
    top: 10px;
    right: 10px;
    font-size: 20px;
    cursor: pointer;
}
</style>
