<template>
    <div class="container">
        <!-- Page content -->
        <ul class="menu-list">
            <li v-for="menu in menus" :key="menu.slug" class="menu-item">
                <NuxtLink :to="`/menus/${menu.slug}`" class="menu-link">
                    {{ menu.name }}
                </NuxtLink>
            </li>
        </ul>
    </div>
</template>

<script setup>
import menus from '~/src/pdfList.json'; // make sure you have a json file containing your menu data
</script>

<style scoped>
.container {
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    background-color: #f7f8fc;
    padding: 20px;
}

.menu-list {
    list-style: none;
    padding: 0;
    max-width: 600px;
    width: 100%;
}

.menu-item {
    margin: 10px 0;
    background-color: #fff;
    border-radius: 10px;
    overflow: hidden;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    perspective: 1000px;
}

.menu-link {
    display: block;
    padding: 250px 20px 30px 20px;
    text-decoration: none;
    color: #ffffff;
    font-size: 3.2rem;
    background: linear-gradient(45deg, #6a11cb 0%, #2575fc 100%);
    transform: rotateX(0deg);
    transition: transform 0.5s, background-color 0.3s, padding 1s, margin 1s;
}

.menu-link:hover {
    padding: 90px 200px 90px 100px;


    background: linear-gradient(45deg, #2575fc 0%, #6a11cb 100%);
    /* transform: rotateX(20deg); */
}

/* Keyframes for the link background animation */
@keyframes backgroundSlide {
    0% {
        background-position: 0 0;
    }

    100% {
        background-position: 100% 100%;
    }
}

.menu-link::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: linear-gradient(120deg, transparent, #fff, transparent);
    z-index: 1;
    transition: opacity 0.3s;
    opacity: 0;
}

.menu-link:hover::before {
    opacity: 0.1;
    animation: backgroundSlide 3s linear infinite;
}

/* Transition for the PDF items on hover */
.menu-item:hover .menu-link {
    color: #f7f8fc;
}
</style>