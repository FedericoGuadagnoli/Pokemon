<script>
import AppLoader from '../AppLoader.vue';
import { store } from '../../data/store';
import PokemonCard from './PokemonCard.vue';
export default {
    name: 'PokemonList',
    components: { PokemonCard, AppLoader },
    data() {
        return {
            store
        }
    },
};
</script>

<template>
    <appLoader v-if="store.isLoading"></appLoader>
    <div v-else class="list-container">
        <div class="row justify-content-center gy-5 pb-3">
            <div v-for="pokemon in store.pokemons" :key="pokemon.id" class="col">
                <PokemonCard :pokemon="pokemon" :color="pokemon.color"></PokemonCard>
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>
.list-container {
    height: 800px;
    width: 90%;
    margin: 0 auto;
    overflow-y: scroll;
    background-color: rgb(75, 75, 75);

    .row {
        width: 100%;
        margin: 0;

        .col {
            flex-basis: 20%;
            height: 20rem;

        }
    }
}
</style>