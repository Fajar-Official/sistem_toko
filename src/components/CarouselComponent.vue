<template>
    <div class="carousel">
        <!-- Navigation -->
        <div class="navigate" v-if="navigationEnabled">
            <div @click="prevSlide" class="toggle-page left">
                <i class="fas fa-chevron-left"></i>
            </div>
            <div @click="nextSlide" class="toggle-page right">
                <i class="fas fa-chevron-right"></i>
            </div>
        </div>

        <!-- Pagination -->
        <div class="pagination" v-if="paginationEnabled">
            <span @click="goToSlide(index)" v-for="(slide, index) in getSlideCount" :key="index"
                :class="{ active: index + 1 === currentSlide }" />
        </div>
        <slot :currentSlide="currentSlide" />
    </div>
</template>

<script setup>
import { onMounted, ref } from 'vue';
const props = defineProps(["startAutoPlay", "timeOut", "navigation", "pagination"])

const currentSlide = ref(1);
const getSlideCount = ref(null);
const autoPlayEnabled = ref(props.startAutoPlay === undefined ? true : props.startAutoPlay);
const timeoutDuration = ref(props.timeOut === undefined ? 5000 : props.timeOut);
const paginationEnabled = ref(props.pagination === undefined ? true : props.pagination);
const navigationEnabled = ref(props.navigation === undefined ? true : props.navigation);
// Next Slide
const nextSlide = () => {
    if (currentSlide.value === getSlideCount.value) {
        currentSlide.value = 1;
        return;
    }
    currentSlide.value += 1;
}
// Prev Slide
const prevSlide = () => {
    if (currentSlide.value === 1) {
        currentSlide.value = 1;
        return;
    }
    currentSlide.value -= 1;
}
// Go to Slide
const goToSlide = (index) => {
    currentSlide.value = index + 1;
}
// AutoPlay
const autoPlay = () => {
    setInterval(() => { nextSlide(); }, timeoutDuration.value)
}
if (autoPlayEnabled.value) {
    autoPlay();
}

onMounted(() => {
    getSlideCount.value = document.querySelectorAll('.slide').length
    console.log("Get Slide Count : " + getSlideCount.value);
})


</script>

<style scoped>
.navigate {
    height: 100%;
    width: 100%;
    position: absolute;
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 100;


    .toggle-page {
        display: flex;
        flex: 1;
    }

    .right {
        justify-content: flex-end;
    }

    i {
        cursor: pointer;
        display: flex;
        align-items: center;
        justify-content: center;
        border-radius: 50%;
        width: 40px;
        height: 40px;
        background-color: #6347c7;
        color: #fff;
    }
}

.pagination {
    z-index: 100;
    position: absolute;
    bottom: 24px;
    width: 100%;
    display: flex;
    gap: 16px;
    justify-content: center;
    align-items: center;

    span {
        cursor: pointer;
        width: 20px;
        height: 20px;
        border-radius: 50%;
        background-color: #fff;
        box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.1), 0 1px 2px 0 rgba(0, 0, 0, 0.06);
    }

    .active {
        background-color: #6347c7;
    }
}
</style>
