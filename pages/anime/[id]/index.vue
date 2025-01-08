<template>
    <h1>MyAnime</h1>
</template>

<script lang="ts" setup>
definePageMeta({
    layout: "anime-page"
})

const fetched = inject('concernedAnime');

const anime = ref(null);

watchEffect(() => {
    anime.value = fetched?.value?.data || null;
})

</script>

<style>

</style>