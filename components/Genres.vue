<template>
    <form @submit.prevent="emits('filterGenre', genre.join(','))">
        <button type="submit" id="buttonGenres">Filtrer</button>
        <div class="genres">
            <label v-for="g in genres" :key="g.id" :for="g.id"><input type="checkbox" :name="g.id" :id="g.id" @change="modifyGenre(g.id)"> {{ g.label }}</label>
        </div>
    </form>
</template>

<script setup>

const emits = defineEmits(['filterGenre']);

const genre = ref([]);

const genres = [
    { label: "Action", id: "1" },
    { label: "Adventure", id: "2" },
    { label: "Comedy", id: "4" },
    { label: "Drama", id: "7" },
    { label: "Fantasy", id: "10" },
    { label: "Game", id: "11" },
    { label: "Historical", id: "14" },
    { label: "Horror", id: "15" },
    { label: "Magic", id: "17" },
    { label: "Martial Arts", id: "18" },
    { label: "Mecha", id: "19" },
    { label: "Mystery", id: "21" },
    { label: "Police", id: "23" },
    { label: "Psychological", id: "24" },
    { label: "Romance", id: "25" },
    { label: "School", id: "27" },
    { label: "Shounen", id: "31" },
    { label: "Slice of Life", id: "32" },
    { label: "Sports", id: "34" }
];


const modifyGenre = (id) => {

    const inside = genre.value.includes(id);

    if(inside) {
        genre.value = genre.value.filter(i => i !== id);
    }
    else {
        genre.value = [...genre.value, id];
    }
}


</script>

<style scoped>

form {
    display: flex;
    flex-direction: column;
}

#buttonGenres {
    margin: 10px;
    padding: 10px 5px;

    color: white;
    background-color: #0f172a;

    border: none;
    border-radius: 10px;

    max-width: 100px;
    min-height: 30px;

    font-size: 17px;
    font-family: 'Times New Roman', Times, serif;

    cursor: pointer;
}

.genres input {
    margin: 10px; 
}

.genres {
    display: grid;
    grid-template-columns: repeat(7, 1fr);
}

</style>