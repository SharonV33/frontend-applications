<template>
    <div>
        <section class="buttons">
            <section id="workingButtons">
                <button id="DR" v-on:click="click('DR')">Drenthe</button>
                <button id="FL" v-on:click="click('FL')">Flevoland</button>
                <button id="GR" v-on:click="click('GR')">Groningen</button>
                <button id="FR" v-on:click="click('FR')">Friesland</button>
                <button id="overview" v-on:click="click('overview')">Nederland</button>
                <button id="compare" v-on:click="click('compare')">Vergelijk provincies</button>
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
        methods: {

            click: function(id) {
                alert(id)
            }
        },
    }
</script>

<style scoped>
    .buttons {
        display: flex;
        width: 50%;
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

</style>