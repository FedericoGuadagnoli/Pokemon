<script>
export default {
    name: 'AppHeader',
};
</script>

<template>
    <header class="my-5">
        <div class="navbar mx-3">
            <div class="col-auto d-flex gap-3">
                <div class="circle bg-primary"></div>
                <div class="circle bg-danger"></div>
                <div class="circle bg-warning"></div>
                <div class="circle bg-success"></div>
            </div>
            <div class="col-auto">
                <figure class="m-0">
                    <img src="../../public/img/pokemon.png" alt="pokemon">
                </figure>
            </div>
        </div>
    </header>
</template>

<style lang="scss" scoped>
.col-auto {
    .circle {
        height: 4rem;
        width: 4rem;
        border-radius: 50%;
        border: 5px solid white;

        &.circle:first-of-type {
            height: 7rem;
            width: 7rem;
        }
    }

    figure {
        img {
            height: 8rem;
            width: auto;
        }
    }
}
</style>