<template>
    <div>
        <header>
                <h1>
                    <NuxtLink to="/">myAnimeSafe</NuxtLink>
                </h1>
        </header>
        <main>
            <slot />
        </main>
        <footer>
            <p>myAnimeSafe. Since 2025</p>
        </footer>
    </div>
</template>

<script setup>

const router = useRoute();

const { id } = router.params;


const anime = ref(null);

const fetchAnime = async () => {
    const { data, error } = await useFetch(`https://api.jikan.moe/v4/anime/${id}`);
    if (error.value) {
        console.error('Erreur lors de la récupération des données :', error.value);
    } else {
        anime.value = data.value;
    }
};

watchEffect(() => {
    fetchAnime();
})



provide('concernedAnime', anime);

</script>

<style scoped>


header, footer {

    display: flex;
    justify-content: center;
    align-items: center;

    font-weight: bold;
}


</style>