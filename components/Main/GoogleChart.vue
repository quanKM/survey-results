<template>
    <div>
        <no-ssr>
            <GChart
                :settings="{packages: ['bar']}"
                :data="chartData"
                :options="chartOptions"
                :create-chart="(el, google) => new google.charts.Bar(el)"
                @ready="onChartReady"
            />
        </no-ssr>
    </div>
</template>


<script>
    import { GChart } from "vue-google-charts"
    import _max from "lodash/max"

    export default {
        components: {
            GChart
        },

        props: {
            chartData: {
                type: Array
            }
        },

        data() {
            return {
                chartsLib: null,
                maxPercentageValue: 30
            }
        },

        computed: {
            chartOptions() {
                if (!this.chartsLib) return null
                return this.chartsLib.charts.Bar.convertOptions({
                    bars: "horizontal",
                    bar: { groupWidth: "50%" },
                    height: 400,
                    hAxis: {
                        format: "#'%'",
                        maxValue: 15,
                        minValue: 0,
                        viewWindow: {
                            max: this.maxPercentageValue,
                            min: 0
                        }
                    },
                    legend: { position: "none" },
                    tooltip: { isHtml: true },
                    colors: ["#7570b3"],

                })
            }
        },
        mounted() {
            let array =  this.chartData.map(o => o[1]).slice(1)
            this.maxPercentageValue = _max(array) <= 50 ? _max(array) : 100
        },
        methods: {
            onChartReady(chart, google) {
                this.chartsLib = google
            }
        }
    }
</script>
