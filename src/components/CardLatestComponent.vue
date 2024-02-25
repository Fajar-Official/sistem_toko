<template>
    <div>
        <div class="card">
            <img :src="item.photo" alt="Product Image" />
        </div>
    </div>
</template>

<script>
export default {
    props: {
        item: {
            type: Object,
            required: true,
        },
    },
};
</script>

<style scoped>
.card {
    text-align: center;
    margin: 10px;
    padding: 15px;
    border: 1px solid #ddd;
    border-radius: 8px;
    display: flex; 
    flex-direction: column; 
    align-items: center; 
}

.card img {
    margin-bottom: 8px;
    width: 100%;
    max-height: 150px;
    object-fit: cover;
    border-radius: 8px;
}
</style>
