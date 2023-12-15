<!-- <template>
    <div>
        <agile :settings="carouselSettings">
            <div v-for="(item, index) in carouselItems" :key="index">
                <img :src="item.image" alt="Carousel Image" />
            </div>
        </agile>
    </div>
</template>

<script setup>
import Agile from 'vue-agile';
import 'vue-agile/dist/VueAgile.css';

const carouselItems = [
    {
        title: 'Item 1',
        description: 'Description for Item 1',
        image: 'https://picsum.photos/800/400?random=1',
    },
    {
        title: 'Item 2',
        description: 'Description for Item 2',
        image: 'https://picsum.photos/800/400?random=2',
    },
    {
        title: 'Item 3',
        description: 'Description for Item 3',
        image: 'https://picsum.photos/800/400?random=3',
    },
];

const carouselSettings = {
    slidesToShow: 1,
    slidesToScroll: 1,
    autoplay: true,
    autoplaySpeed: 2000, // Ganti sesuai kebutuhan Anda
    arrows: true,
    dots: true,
    // Tambahan konfigurasi lainnya sesuai kebutuhan
};
</script>

<style scoped>
/* Gaya carousel khusus di sini jika diperlukan */
/* PASTIKAN GAYA DI SINI SESUAI DENGAN KEINGINAN ANDA */

/* Gaya untuk dot pagination */
.agile-dots {
    position: absolute;
    bottom: 20px;
    width: 100%;
    display: flex;
    justify-content: center;
}

.agile-dot {
    width: 10px;
    height: 10px;
    margin: 0 5px;
    background-color: #bbb;
    border-radius: 50%;
    cursor: pointer;
}

.agile-dot.agile-dot-active {
    background-color: #717171;
}
</style> -->
