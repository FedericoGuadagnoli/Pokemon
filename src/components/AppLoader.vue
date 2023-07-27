<script>
export default {
    name: 'AppLoader',
};
</script>

<template>
    <div class="loader d-flex flex-column justify-content-center align-items-center">
        <figure class="m-0 h-75">
            <img class="h-100" src="../../public/img/pokeball.gif" alt="pokeball">
        </figure>
        <p class=" loading text-uppercase text-danger fw-bolder">sto catturando i pokemon!</p>
    </div>
</template>

<style lang="scss" scoped>
.loader {
    position: fixed;
    z-index: 1;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: white;

    .loading {
        font-size: 5rem;
    }
}
</style>