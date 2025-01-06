<template>
    <div>
        <header>
            <nav>
                <h1>
                    <NuxtLink to="/">myAnimeSafe</NuxtLink>
                </h1>
                <SearchBar v-model="name" />
                <!-- <NuxtLink to="/profile">Profile</NuxtLink> -->
            </nav>
            <Genres @filterGenre="modifyGenre" />
        </header>
        <main>
            <slot />
        </main>
        <footer>
            <Pagination @previous="previous" @next="next" @first="first" @last="last" />
            <p>myAnimeSafe. Since 2025</p>
        </footer>
    </div>
</template>

<script setup>
import SearchBar from '../components/SearchBar.vue';
import Pagination from '../components/Pagination.vue';
import Genres from '../components/Genres.vue';


// Code for managing pagination

const page = ref(1);

const previous = () => {
    console.log("took here")
    if(page.value >= 2) {
        page.value = page.value - 1;
    }
}

const next = () => {
    if(page.value <= 1117) {
        page.value = page.value + 1;
    }
}

const first = () => page.value = 1;
const last = () => page.value = 1118;




// Managing the filtering

const name = ref('');
const genre = ref('');

const modifyGenre = (genres) => {
    console.log("Took here")
    genre.value = genres;
}

const URL =  computed(() => {
    const filterName = (name.value !== '') ? `&q=${name.value.replace(' ', '_')}` : '';
    const filterGenre = (genre.value !== '') ? `&genres=${genre.value}` : '';
    return `https://api.jikan.moe/v4/anime?order_by=start_date&sort=desc&page=${page.value}&limit=25` + filterName + filterGenre;
});

const animes = ref([]);

const fetchAnimes = async () => {
    const { data, error } = await useFetch(URL.value);
    if (error.value) {
        console.error('Erreur lors de la récupération des données :', error.value);
    } else {
        animes.value = data.value;
    }
};

watchEffect(() => {
    fetchAnimes();
});

provide('animes', animes);


</script>

<style>
body {
    background-color: #090f29;
    color: white;

    margin: 0;
    padding: 0;

    font-size: 17px;
    font-family: 'Times New Roman', Times, serif;
}

a {
    text-decoration: none;
    color: white;

    font-weight: bold;
}

header, footer {
    min-height: 30px;
    background-color: #020617;

    padding: 10px;
}

main {
    min-height: 430px;
}

footer {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

    font-weight: bold;
}

nav {
    display: grid;
    grid-template-columns: 25% 1fr 20%;
    grid-template-rows: 100%;

    justify-items: center;
    align-items: center;
}

</style>