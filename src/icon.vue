<template>
    <svg class="icon" aria-hidden="true">
        <use :xlink:href="`#i-${name}`"></use>
    </svg>
</template>

<script>
    export default {
        props: ['name']
    }
</script>

<style lang="scss">
    .icon {
        width: 1em;
        height: 1em;
    }
</style>