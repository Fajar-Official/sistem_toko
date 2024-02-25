
<template>
    <footer class="footer">
        <div class="container">
            <div class="footer-top">
                <div class="footer-section">
                    <p class="text-talk">Talk to Us Now!</p>
                    <p class="title-content">Contact Us</p>
                    <div class="content">
                        <p class="address">Jl. Palagan km 10 Rejodani, Ngaglik Sleman Yogyakarta</p>
                        <p class="phone"><i class="fa fa-phone"></i> 0877-3821-0660</p>
                    </div>
                </div>
                <div class="footer-section">
                    <p class="text-talk">Talk to Us Now!</p>
                    <p class="title-content">OUR SERVICES</p>
                    <div class="content">
                        <ul>
                            <li><a href="https://sistemtoko.com/how-to-order">CARA PEMBELIAN</a></li>
                            <li><a href="https://sistemtoko.com/f-a-q">F.A.Q</a></li>
                            <li><a href="https://sistemtoko.com/konfirmasi-pembayaran">KONFIRMASI PEMBAYARAN</a></li>
                            <li><a href="https://sistemtoko.com/about-us">TENTANG </a></li>
                            <li><a href="https://sistemtoko.com/term-condition">SYARAT & KETENTUAN</a></li>
                            <li><a href="https://sistemtoko.com/pengembalian-dan-penukaran">PENGEMBALIAN DANPENUKARAN</a>
                            </li>
                        </ul>
                    </div>
                </div>

                <div class="footer-section">
                    <p class="text-talk">Talk to Us Now!</p>
                    <p class="title-content">FOLLOW US</p>
                    <div class="content">
                        <div class="social">
                            <a href="https://www.facebook.com/"><i class="fa-brands fa-facebook-f"></i></a>
                            <a href="#"><i class="fa-brands fa-twitter"></i></a>
                            <a href="https://www.instagram.com/"><i class="fa-brands fa-instagram"></i></a>
                        </div>
                    </div>
                </div>
            </div>

            <div class="footer-bottom">
                <div class="container">
                    <div class="">
                        <span>supported by <a href="http://sistemtoko.com">sistemtoko</a></span>.
                        Allright reserved
                    </div>
                </div>
            </div>
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
    margin-top: 5rem;
}
.text-talk{
    font-size: large;
    color: #00BD7E;
    font-family: 'Courier New', Courier, monospace;

}
.footer-top {
    display: flex;
    justify-content: space-around;
    flex-grow: 1; 
}

.footer-bottom {
    text-align: center;
}

.footer-section {
    flex: 1;
}

.title-content {
    font-size: medium;
    margin-bottom: 10px;
    font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif ;
}

.content {
    line-height: 1.5;
}

a {
    color: #fff;
    text-decoration: none;
    margin-right: 10px;
}

input {
    padding: 8px;
    width: 70%;
    margin-right: 10px;
}

button {
    padding: 8px;
    background-color: #fff;
    color: #333;
    cursor: pointer;
    border: none;
}
</style>
