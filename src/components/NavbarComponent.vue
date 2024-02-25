<template>
    <nav>
      <div class="nav-inner">
        <div class="logo">
          <img src="@/assets/logo.svg" width="10%">
        </div>
        <div class="menu">
          <router-link to="/" class="text-links">Home</router-link>
          <div class="dropdown" @mouseover="showDropdown" @mouseleave="hideDropdown">
            <span class="text-links">Product</span>
            <div class="dropdown-content" v-show="isDropdownVisible">
              <router-link to="/product">All Products</router-link>
              <router-link v-for="cat in categories" :key="cat.product_category_id" :to="`/category/${cat.keyword_name}`">
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

.nav-inner {
  display: flex;
  justify-content: space-between; 
  align-items: center;
  padding: 1rem;
  width: 100%;
}

.logo {
  flex: 1; 
}

.menu {
  flex: 1;
  display: flex;
  gap: 1rem;
  justify-content: flex-start; 
  align-items: center;
}

.icons {
  flex: 1; 
  display: flex;
  gap: 1rem;
  justify-content: flex-end;
}

.text-links {
  font-size: large;
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

.icons i {
  font-size: 24px;
}

  </style>
  