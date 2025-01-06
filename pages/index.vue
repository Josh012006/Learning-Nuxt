<template>
    <div class="home">
        <AnimeCard v-for="anime in tab" :key="anime.mal_id" :anime="anime" />
    </div>
</template>

<script setup>
import AnimeCard from "../components/AnimeCard.vue"

const animes = inject('animes');

const tab = ref([]);

watchEffect(() => {
    tab.value = animes?.value?.data || [];;
})

</script>

<style scoped>

.home {
    display: grid;
    grid-template-columns: repeat(5, 1fr);

    gap: 15px;
    margin: 10px;
}

</style>