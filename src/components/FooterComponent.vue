<template>
    <footer class="footer">
        <div class="footer-section">
            <h3>Contact Us</h3>
            <p>Email: info@example.com</p>
            <p>Phone: +1 (123) 456-7890</p>
        </div>

        <div class="footer-section">
            <h3>Quick Links</h3>
            <router-link to="/">Home</router-link>
            <router-link to="/">About</router-link>
            <router-link to="/">Contact</router-link>
        </div>

        <div class="footer-section">
            <h3>Follow Us</h3>
            <a href="https://twitter.com/example" target="_blank" rel="noopener noreferrer">Twitter</a>
            <a href="https://www.facebook.com/example" target="_blank" rel="noopener noreferrer">Facebook</a>
            <a href="https://www.instagram.com/example" target="_blank" rel="noopener noreferrer">Instagram</a>
        </div>

        <div class="footer-section">
            <h3>Newsletter</h3>
            <p>Subscribe to our newsletter for updates.</p>
            <input type="email" placeholder="Enter your email" />
            <button>Subscribe</button>
        </div>

        <div class="footer-section">
            <h3>Location</h3>
            <p>123 Main Street, Cityville, Country</p>
        </div>
    </footer>
</template>

<script setup>
</script>

<style scoped>
.footer {
    background-color: #333;
    color: #fff;
    padding: 20px;
    display: flex;
    justify-content: space-around;
    flex-wrap: wrap;
}

.footer-section {
    margin-bottom: 20px;
}

.footer a {
    color: #fff;
    text-decoration: none;
    margin-right: 10px;
}

.footer input {
    padding: 8px;
    width: 70%;
    margin-right: 10px;
}

.footer button {
    padding: 8px;
    background-color: #fff;
    color: #333;
    cursor: pointer;
    border: none;
}
</style>
