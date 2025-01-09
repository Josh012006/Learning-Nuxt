<template>
    <div v-if="anime">
        <img :src="anime.images.jpg.image_url" alt="poster">
        <h3>
            <span v-for="title in anime.titles" :key="title">{{ title.title }} | </span>
        </h3>

        <div>
            <h4>Studio: </h4>
            <span v-for="studio in anime.studios" :key="studio"> {{ studio.name }} |</span>
        </div>
        <div>
            <h4>Genres: </h4>
            <span v-for="genre in anime.genres" :key="genre"> {{ genre.name }} | </span>
        </div>
        <NuxtLink :href="anime.url">See on My Anime List</NuxtLink>
        <NuxtLink :href="anime.trailer.url">See the trailer</NuxtLink>
        <span>Status: {{ anime.status }}</span>
        <span>Score: {{ anime.score }}</span>
        <p>{{ anime.synopsis }}</p>
    </div>
</template>

<script lang="ts" setup>
definePageMeta({
    layout: "anime-page"
})

const fetched = inject('concernedAnime');

const anime = ref(null);

watchEffect(() => {
    anime.value = fetched?.value?.data || null;

    console.log(anime.value);
})

</script>

<style>

</style>