<template>
    <input type="text" name="searchBar" id="searchBar" v-model="filterOption" placeholder="Search an anime...">
</template>

<script setup>

const filterOption = defineModel();

</script>



<style scoped>
input {
    border: none;
    border-radius: 20px;

    height: 20px;

    min-width: 80%;

    color: white;
    background-color: #0f172a;

    font-size: 17px;
    font-family: 'Times New Roman', Times, serif;
    padding: 10px 30px;
}

input::placeholder {
    color: white;
}

</style>