<template>
    <div class="close" @click="$emit('closeModalFromOtherClass')">

    </div>
</template>

<script>
    export default {
        name: 'CloseModal',
        };
</script>

<style lang="scss" scoped>
    .close {
        width: 100%;
        height: 100%;
        position: fixed;
        z-index: 99;
        background-color: lightgray;
        opacity: 0.2;
    }
</style>
