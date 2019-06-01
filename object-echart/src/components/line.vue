<template>
    <div id>
        <h3>进来了</h3>
        <div ref="main" style="width: 600px;height:400px;margin:0 auto;"></div>
    </div>
</template>
 
<script>
import echarts from "echarts";
export default {
    name: "",
    props: {},
    components: {},
    data() {
        return {
            myChart: ""
        };
    },
    mounted() {
        this.renderChart();
    },
    computed: {},
    methods: {
        renderChart() {
            let main = this.$refs.main;
            this.myChart = echarts.init(main);
            let myChart = this.myChart;
            let option = {
                xAxis: {
                    type: "category",
                    data: ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"]
                },
                yAxis: {
                    type: "value"
                },
                series: [
                    {
                        data: [820, 932, 901, 934, 1290, 1330, 1320],
                        type: "line",
                        // 标记的图形。
                        symbol: "triangle",
                        symbolSize: 10,
                        label: {
                            show: true
                        }
                    }
                ],
                tooltip: {
                    trigger: 'axis',
                    axisPointer: {
                        type: "line"
                    }
                }
            };

            myChart.setOption(option);
            // setInterval(()=>{
            //     this.randomNum();
            // },2000);
        },
        randomNum() {
            let symbolArr = [
                "circle",
                "rect",
                "roundRect",
                "triangle",
                "diamond",
                "pin",
                "arrow",
                "none"
            ];

            let myChart = this.myChart;
            let num = Math.round(Math.random() * symbolArr.length);
            let option = myChart.getOption();
            option.series[0].symbol = symbolArr[num];
            myChart.setOption(option);
        }
    },
    watch: {},
    filters: {}
};
</script>
 
<style></style>
 