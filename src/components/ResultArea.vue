<template>
    <Profiles v-for="(c, i) in filteredCharacters" :key="i" :profile="c"></Profiles>
    <el-result
        icon="primary"
        title="找不到相關參加者"
        v-show="!filteredCharacters.length">
      </el-result>
</template>

<script setup>
import { ref, onMounted, computed } from 'vue';
import Profiles from './Profiles.vue';

const props = defineProps({
    keyword: String
})

const characters = ref([])

onMounted(async () => {
    const res = await fetch("/characters.json");
    characters.value = await res.json();
});

const filteredCharacters = computed(() => {
    if(!props.keyword) return characters.value;
    return characters.value.filter(person => 
        Object.values(person).some(field => 
            String(field).includes(props.keyword)
        )
    )
})
</script>

<style scoped></style>