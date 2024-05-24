<template>
    <div>
        <h1 style="padding-left: 10px;">Attractions</h1>
        <div class="grid-contanier">
            <div class="card" v-for="item in items">
                <img :src="item.coverimage" :alt="item.name" style="width:100%">
                <div class="CardContainer">
                    <h4><b>{{ item.name }}</b></h4>
                    <p>
                        <NuxtLink :to="'/attractions/' + item.id">
                            Read More
                        </NuxtLink>
                    </p>
                </div>
                <br>
            </div>
        </div>

    </div>
</template>

<script setup>
import { ref } from 'vue'
const items = ref([])

fetch('https://www.melivecode.com/api/attractions')
    .then(res => res.json())
    .then((result) => {
        items.value = result
        console.log(result)
    })

</script>

<style scoped>
.grid-contanier {
    display: grid;
    grid-column-gap: 0.5rem;
    grid-row-gap: 0.5rem;
}

@media(min-width: 576px) {
    .grid-contanier {
        grid-template-columns: repeat(1, 1fr);
    }
}

@media(min-width: 992px) {
    .grid-contanier {
        grid-template-columns: repeat(3, 1fr);
    }
}

.card {
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    transition: 0.3s;
}

.card:hover {
    box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2);
}

.CardContainer {
    padding: 2px 16px;
}
</style>