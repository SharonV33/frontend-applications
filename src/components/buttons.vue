<template>
    <div>
        <section class="buttons">
            <section id="workingButtons">
                <button id="DR" v-on:click="changeProvince('DR')" :class="currentProvince === 'DR' ? 'active' : ''">Drenthe</button>
                <button id="FL" v-on:click="changeProvince('FL')" :class="currentProvince === 'FL' ? 'active' : ''">Flevoland</button>
                <button id="GR" v-on:click="changeProvince('GR')" :class="currentProvince === 'GR' ? 'active' : ''">Groningen</button>
                <button id="FR" v-on:click="changeProvince('FR')" :class="currentProvince === 'FR' ? 'active' : ''">Friesland</button>
                <button id="overview" v-on:click="changeProvince('finalData')">Nederland</button>
                <button id="compare" v-on:click="changeProvince('allProvinces')">Vergelijk provincies</button>
            </section>

            <section class="disabledButtons">
                <button id="NH">Noord Holland</button>
                <button id="ZH">Zuid Holland</button>
                <button id="UT">Utrecht</button>
                <button id="GD">Gelderland</button>
                <button id="OV">Overijsel</button>
                <button id="NB">Noord Brabant</button>
                <button id="LB">Limburg</button>
                <button id="ZL">Zeeland</button>
            </section>
            <p>Black buttons are provinces currently unavalible due to a lack of data</p>
        </section>
    </div>
</template>

<script>
    // import d3 from "d3";
    export default {
        name: "buttons",
        props: {
            currentProvince: String
        },
        data() {
            return{}
        },
        methods: {
            changeProvince: function(id) {
                this.$emit('change-province', id)
            }
        },
    }
</script>

<style scoped>
    .buttons {
        display: flex;
        flex-wrap: wrap;
    }
    .buttons section {
        width: 80%;
        text-align: center;
    }
    button {
        height: 3em;
        width: 12em;
        margin: 1em 3em;
        background-color: #ffffff;
        border: 1px solid #575757;
        color: #575757;
    }
    #NH, #ZH, #UT, #OV, #NB, #LB, #ZL, #GD{
        background-color: black;
    }

    .active {
        background-color: #98abc5;
    }

</style>