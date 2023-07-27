<script>
export default {
    name: 'PokemonCard',
    props: {
        pokemon: Object,
        color: String
    }
};
</script>

<template>
    <div :class="[color, 'card d-flex flex-column align-items-center justify-content-between py-3']">
        <figure class="m-0">
            <img :src="pokemon.imageUrl" :alt="pokemon.name">
        </figure>
        <figcaption class="px-1 d-flex flex-column align-items-center justify-content-between text-center">
            <span class="fs-3">#{{ pokemon.number }}</span>
            <h4 class="fw-bolder">{{ pokemon.name }}</h4>
            <span class="fst-italic">{{ pokemon.type1 }} {{ pokemon.type2 }}</span>
        </figcaption>
    </div>
</template>

<style lang="scss" scoped>
.card {
    height: 100%;

    &.Blue {
        background-color: dodgerblue;
    }

    &.Purple {
        background-color: purple;
    }

    &.Pink {
        background-color: pink;
    }

    &.Brown {
        background-color: brown;
    }

    &.Yellow {
        background-color: yellow;
    }

    &.Red {
        background-color: red;
    }

    &.Green {
        background-color: greenyellow;
    }

    &.Black {
        background-color: black;
        color: white;
    }

    figure {
        height: 50%;

        img {
            width: 100%;
            height: 100%;
        }
    }

    figcaption {
        height: 50%;
    }
}
</style>