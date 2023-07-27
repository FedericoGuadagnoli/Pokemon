<script>
export default {
    name: 'SearchForm',
    props: {
        typologies: Array,
        searchText: String,
        clearText: String,
        inputText: String
    },
    data() {
        return {
            selectedType: '',
            filterText: ''
        }
    },
    emits: ['selected', 'search', 'clear', 'filtered-text']
};
</script>

<template>
    <form @submit.prevent>
        <select v-model="selectedType" @change="$emit('selected', selectedType)" class="my-5">
            <option v-for=" (typologie, i) in  typologies " :key="typologie" :value="typologie">{{
                typologie }}</option>
        </select>
        <button v-if="selectedType" @click="$emit('search')" class="btn btn-success ms-3">{{ searchText }}</button>
        <input type="text" class="mx-3 w-25 px-3" v-model.trim="filterText" :placeholder="inputText"
            @keyup.enter="$emit('filtered-text', filterText)">
        <button v-if="selectedType" @click="$emit('clear')" class="btn btn-warning">{{ clearText }}</button>
    </form>
</template>

<style></style>