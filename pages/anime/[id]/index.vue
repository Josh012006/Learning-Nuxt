<template>
    <div v-if="anime">
        <div class="heading">
            <div class="div-img">
                <img :src="anime.images.jpg.image_url" alt="poster">
            </div>
            <div>
                <h3 class="titles">
                    <span v-for="title in anime.titles" :key="title">{{ title.title }} | </span>
                </h3>
                <div class="production">
                    <div>
                        <h4>Studios: </h4>
                        <span v-for="studio in anime.studios" :key="studio"> {{ studio.name }} |</span>
                    </div>
                    <div>
                        <h4>Genres: </h4>
                        <span v-for="genre in anime.genres" :key="genre"> {{ genre.name }} | </span>
                    </div>
                    <div>
                        <h4>Themes: </h4>
                        <span v-for="theme in anime.themes" :key="theme"> {{ theme.name }} | </span>
                    </div>
                </div>
            </div>
        </div>
        <div class="anime-info">
            <span><b>Status:</b> {{ anime.status }}</span>
            <span><b>Score:</b> {{ anime.score }}</span>
            <p><b>Synopsis:</b> {{ anime.synopsis }}</p>
        </div>
        <div class="anime-links">
            <NuxtLink :href="anime.url">See on My Anime List</NuxtLink>
            <NuxtLink :href="anime.trailer.url">See the trailer</NuxtLink>
        </div>
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

<style scoped>
.heading {
    display: grid;
    grid-template-columns: 35% 1fr;
    justify-items: center;
    align-items: center;
}

.div-img {
    background-color: #213073;

    width: 100%;
    height: 100%;

    text-align: center;
}

.div-img img {
    border-radius: 7px;

    height: 100%;
}

.titles {
    text-align: center;
}

.production {
    display: flex;
    justify-content: space-around;
    align-items: center;
}

.production div {
    padding: 10px;
}

.anime-info {
    display: flex; 
    flex-direction: column;
    justify-content: space-around;

    padding: 10px 5px;
}

.anime-links {
    display: flex;
}

.anime-links a {
    padding: 10px 20px;
    margin: 30px;

    color: white;
    background-color: #213073;

    border-radius: 7px;
}
</style>