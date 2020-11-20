<template>
    <h1 v-on:click="showData">pie</h1>
</template>

<script>
    export default {
        name: "pie",
        props: parkingdata,
        data: {
            parkingdata
        },
        methods: {
            showData: async function () {
                const data = await parkingdata
                console.log(data)
            }
        },
    }
</script>

<style scoped>

</style>