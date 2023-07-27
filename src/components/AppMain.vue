<script>
import PokemonList from './pokemons/PokemonList.vue';
export default {
    name: 'AppMain',
    components: { PokemonList },
};
</script>

<template>
    <main>
        <div class="box rounded-5 d-flex align-items-center">
            <PokemonList></PokemonList>
        </div>

    </main>
</template>

<style lang="scss" scoped>
main {
    .box {
        height: 900px;
        background-color: lightgrey;
    }
}
</style>