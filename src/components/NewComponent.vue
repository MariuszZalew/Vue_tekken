<template>
    <div>
        just me here
        <!-- <IconCommunity /> -->
        {{ msg }}

        <img alt="Vue logo" class="logo" src="@/assets/button/STEAM/2+4.svg" width="125" height="125" />
        <ul>
            <li v-for="a in data" :key="a.damage">{{ a.damage }}</li>
        </ul>
        <pre>
            {{ data[0] }}
        </pre>

        <!-- <img alt="Vue logo" class="logo" src="@/assets/arrow/b.svg" width="125" height="125" /> -->
    </div>
</template>

<script setup lang="ts">
import { onMounted, ref } from 'vue'
// import IconCommunity from './icons/IconCommunity.vue'

// type dataType = {
//     damage: string
//     id: string
//     input: string
//     name: string
// }
const data = ref<any>([])
defineProps<{
    msg: string
}>()
onMounted(() => {
    console.log("I'm mounted bro!")
    fetch('/src/assets/json_movelist/azucena.json')
        .then(raw => raw.json())
        .then(dataFromJSON => data.value = dataFromJSON)
        .catch(e => console.log("error: ", e))
})
</script>

<style scoped></style>