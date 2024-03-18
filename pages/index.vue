<template>
  <div>
    <pre>{{ data.joke }}</pre>
  </div>
</template>

<script setup lang="ts">
const nuxtApp = useNuxtApp();

const { data } = await useFetch<any>('https://icanhazdadjoke.com', {
  headers: {
    Accept: 'application/json',
  },

  getCachedData(key) {
    return nuxtApp.payload[key] || nuxtApp.static.data[key];
  },
});
</script>