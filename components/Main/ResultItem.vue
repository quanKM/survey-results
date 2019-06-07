<template>
    <div :id="answer.name" class="result-item">
        <div class="result-item__title">
            {{ answerTitle }}
        </div>

        <div v-if="answerDescription" class="result-item__description">
            {{ answerDescription }}
        </div>

        <div class="result-item__result">
            <GoogleChart :chart-data="chartData" class="result-item__result-chart" />
        </div>
    </div>
</template>

<script>
    import _upperCase from "lodash/upperCase"
    import _keys from "lodash/keys"
    import _values from "lodash/values"
    import GoogleChart from "./GoogleChart.vue"
    import _toPairs from "lodash/toPairs"

    const descriptions = {
        application_server: "asd",
        database_server: "",
        deploy_tools: "",
        server_os: "",
        deploy_tools: "",
        proxy_server: "",
        program_language: "",
        framework: "",
        serivce: "",
        database_server: "",
        other_tools: ""
    }

    export default {
        components: {
            GoogleChart
        },

        props: {
            answer: {
                required: true,
                type: Object
            }
        },

        data() {
            return {
                descriptions
            }
        },

        computed: {
            answerTitle() {
                return _upperCase(this.answer.name)
            },

            chartData() {
                return [["", "Percentage"], ..._toPairs(this.answer.value)]
            },

            answerDescription() {
                return this.descriptions[this.answer.name] || null
            }
        }
    }
</script>


<style lang="scss">
    .result-item {
        margin-bottom: 50px;

        &__title {
            text-align: center;
            border-bottom: 1px solid black;
            margin-bottom: 20px;
        }

        &__result {
            position: relative;
        }
    }
</style>
