<script setup>

const layout = 'baseLayout'

</script>

<template>
  <div>
    <NuxtRouteAnnouncer />
    <NuxtLayout :name="layout">
      <NuxtPage />
    </NuxtLayout>
  </div>
</template>
