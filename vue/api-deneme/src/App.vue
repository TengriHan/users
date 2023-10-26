<script setup>
import { onMounted, ref } from "vue"

const data = ref([]);

async function fetchData(name) {
  const result = await fetch(`https://dog.ceo/api/breed/${name}/images`)
    .then(data => data.json())
    .then((response) => response.message);

    return result;
}

onMounted(async () => {
  data.value = await fetchData("pug");
})
</script>

<template>
  <img v-for="myData in data" :src="myData" :key="myData">
</template>

<style scoped>
  img{
    max-width: 150px;
    max-height: 150px;
    margin: 5px;
    border: 2px solid gray;
}
</style>