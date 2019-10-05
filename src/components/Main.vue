<template>
    <main>
        <Goods></Goods>
        <Subscribe></Subscribe>
    </main>
</template>

<script>
    import Subscribe from './Subscribe';
    import Goods from './Goods';

    export default {
        name: "Main",
        components: {Subscribe, Goods}
    }
</script>

<style scoped>

</style>