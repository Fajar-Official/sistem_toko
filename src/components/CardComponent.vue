<template>
    <div class="card">
        <img :src="item.photo" alt="Product Image" />
        <p>{{ item.name }}</p>
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
}

.card img {
    width: 100%;
    max-height: 150px;
    object-fit: cover;
    border-radius: 8px;
}

.card p {
    margin-top: 8px;
}
</style>
