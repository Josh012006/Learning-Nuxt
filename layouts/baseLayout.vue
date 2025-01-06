<template>
    <div>
        <header>
            <NuxtLink to="/">myAnimeSafe</NuxtLink>
            <SearchBar v-model="filter" />
        </header>
        <slot></slot>
        <Pagination @previous="previous" @next="next" @first="first" @last="last" />
        <footer>
            myAnimeSafe. Since 2025
        </footer>
    </div>
</template>

<script setup>
import SearchBar from '../components/SearchBar.vue';
import Pagination from '../components/Pagination.vue';


// Code for managing pagination

const page = ref(1);

const previous = () => {
    if(page >= 2) {
        page.value--;
    }
}

const next = () => {
    if(page <= 1117) {
        page.value++;
    }
}

const first = () => page.value = 1;
const last = () => page.value = 1118;





const filter = ref("");

const URL =  computed(() => {
    return `https://api.jikan.moe/v4/anime?order_by=start_date&sort=desc&page=${page.value}&limit=25`;
});

const { data: animesFetched } = useFetch(URL.value);

const animes = computed(() => {
    if(filter.value !== '') {
        return animesFetched.value.filter((anime) => anime.titles[0].title.toLowerCase().startsWith(filter.value.toLowerCase()));
    }
});

provide('animes', animes);

</script>

<style>

</style>