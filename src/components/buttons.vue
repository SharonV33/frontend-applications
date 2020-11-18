<template>
    <div>
        <section class="buttons">
            <section id="workingButtons">
                <button id="DR">Drenthe</button>
                <button id="FL">Flevoland</button>
                <button id="GR">Groningen</button>
                <button id="FR">Friesland</button>
                <button id="overview">Nederland</button>
                <button id="compare">Vergelijk provincies</button>
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
    export default {
        name: "buttons"
    }
</script>

<style scoped>
    .buttons {
        display: flex;
        width: 100%;
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