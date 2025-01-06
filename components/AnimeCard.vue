<template>
    <NuxtLink :to="anime.url">
        <img :src="anime.images.jpg.image_url" alt="anime image" />
        <h3>{{ anime.titles[0].title }}</h3>
    </NuxtLink>
</template>

<script setup>

const props = defineProps({
    anime: Object
})

</script>

<style scoped>

img {
    width: 100%;
    height: 70%;
}

img, a {
    background-color: #181d28;

    border-radius: 7px;
}

h3 {
    padding: 5px;
    text-align: center;
}

</style>