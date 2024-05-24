<template>
    <div>
        <h1>{{ item.name }}</h1>
        <img :src="item.coverimage">
        <p>{{ item.detail }}</p>
    </div>
</template>

<script setup>
import { ref } from 'vue';
const route = useRoute()
const item = ref({})

const id = route.params.id
fetch('https://www.melivecode.com/api/attractions/'+id)
    .then(res => res.json())
    .then((result) => {
        item.value = result.attraction
    })
</script>

<style scoped>

</style>