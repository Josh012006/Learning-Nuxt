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

<style>

</style>