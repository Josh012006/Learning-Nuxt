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

</script>

<style scoped>

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

    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

    font-weight: bold;
}

main {
    min-height: 430px;
}

</style>