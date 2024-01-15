<template>
    <nav>
        <div class="nav-inner">
            <div class="logo">
                <img src="@/assets/logo.svg" alt="" width="10%">
            </div>
            <div class="links">
                <router-link to="/">Home</router-link>
                <div class="dropdown" @mouseover="showDropdown" @mouseleave="hideDropdown">
                    <span>Product</span>
                    <div class="dropdown-content" v-show="isDropdownVisible">
                        <router-link to="/product">All Products</router-link>
                        <router-link v-for="cat in categories" :key="cat.product_category_id"
                            :to="`/category/${cat.keyword_name}`">
                            {{ cat.product_category_name }}
                        </router-link>
                    </div>
                </div>
            </div>
            <div class="icons">
                <i class="fas fa-shopping-cart"></i>
                <i class="fas fa-bell"></i>
                <i class="fas fa-user"></i>
            </div>
        </div>
    </nav>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';

const categories = ref([]);
const isDropdownVisible = ref(false);

onMounted(() => {
    fetchDataCategory();
});

const fetchDataCategory = async () => {
    try {
        const response = await axios.get('https://sistemtoko.com/public/demo/cat');
        categories.value = response.data.aaData;
    } catch (error) {
        console.error('Error fetching category data:', error);
    }
};

const showDropdown = () => {
    isDropdownVisible.value = true;
};

const hideDropdown = () => {
    isDropdownVisible.value = false;
};
</script>

<style scoped>
nav {
    display: flex;
    justify-content: center;
}

nav .nav-inner {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    padding: 1rem;
    background-color: #f0f0f0;
    width: 95%;
}

.logo img {
    max-width: 100%;
    height: auto;
}

.links {
    display: flex;
    gap: 1rem;
    justify-content: center;
    align-items: center;
}

/* Dropdown Styles */
.dropdown {
    position: relative;
}

.dropdown-content {
    display: none;
    position: absolute;
    background-color: #fff;
    box-shadow: 0 8px 16px rgba(0, 0, 0, 0.1);
    z-index: 2;
    margin-top: 8px;
    /* Menambahkan margin atas pada dropdown */
}

.dropdown:hover .dropdown-content {
    display: block;
}

.dropdown-content a {
    padding: 12px;
    text-decoration: none;
    display: block;
    color: #333;
}

.dropdown-content a:hover {
    background-color: #f0f0f0;
}

/* End Dropdown Styles */

.icons {
    display: flex;
    gap: 1rem;
    justify-content: flex-end;
    margin-right: 8px;
    /* Menambahkan margin kanan pada icons */
}

.icons i {
    font-size: 24px;
}</style>
