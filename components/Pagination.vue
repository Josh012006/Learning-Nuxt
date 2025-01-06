<template>
    <div>
        <button @click="emits('previous')">Previous Page</button>
        <button @click="emits('first')">First</button>
        <button @click="emits('last')">Last</button>
        <button @click="emits('next')">Next Page</button>
    </div>
</template>

<script setup>

const emits = defineEmits(['previous', 'next', 'first', 'last']);

</script>

<style scoped>
button {
    margin: 10px 20px;
    padding: 10px 15px;

    color: white;
    background-color: #0f172a;

    border: none;
    border-radius: 10px;

    max-width: 200px;
    min-height: 30px;

    font-size: 17px;
    font-family: 'Times New Roman', Times, serif;

    cursor: pointer;
}
</style>