<script>
export default {
    name: 'BasePagination',
    props: {
        prevDisabled: Boolean,
        nextDisabled: Boolean
    },
    emits: ['prev-page', 'next-page']
};
</script>

<template>
    <div class="text-center py-3">
        <button :class="['btn btn-primary text-white me-3', { 'disabled': prevDisabled }]"
            @click="$emit('prev-page')">Precedente</button>
        <button :class="['btn btn-primary text-white', { 'disabled': nextDisabled }]"
            @click="$emit('next-page')">Successiva</button>
    </div>
</template>

<style></style>