<template>
    <div>
        <div class="card">
            <img :src="item.photo" alt="Product Image" />
        </div>
        <div class="details">
            <p>{{ item.name }}</p>
            <p>{{ item.currency }} {{ item.price }}</p>
            <button>ADD TO CART</button>
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

.details {
    margin-top: 8px;
    text-align: center;
}

 button {
    margin-top: 8px;
    padding: 8px 16px;
    background-color: #333;
    color: #fff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    transition: background-color 0.3s;
}

 button:hover {
    background-color: #00BD7E;
}
</style>
