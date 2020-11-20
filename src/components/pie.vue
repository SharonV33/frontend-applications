<template>
    <h1 v-on:click="showData">pie</h1>
</template>

<script>
    export default {
        name: "pie",
        props: data,
        methods: {
            showData: async function (data) {
                const showData = await data
                console.log(showData)
            }
        },
    }
</script>

<style scoped>

</style>