<template>
    <div id>
        <div>
            <canvas ref="cc" width="200" height="200"></canvas>
            <canvas ref="cc2" width="200" height="200"></canvas>
            <canvas ref="cc3" width="200" height="200"></canvas>
            <canvas ref="cc4" width="200" height="200"></canvas>
            <canvas ref="cc5" width="200" height="200"></canvas>
        </div>
    </div>
</template>
 
<script>
var bigengineer = require("../utils/bigengineer.js");
export default {
    name: "",
    props: {},
    components: {},
    data() {
        return {};
    },
    mounted() {
        this.DrawRoundRect();
        this.DrawAOBArc();
        this.DrawQuadraticCurveTo();
        this.DrawbezierCurveTo();
        this.DrawArc();
    },
    computed: {},
    methods: {
        DrawRoundRect() {
            let cc = this.$refs.cc;
            let hb = cc.getContext("2d");
            let A = new Array(55, 55);
            let C = new Array(150, 150);
            hb.beginPath();
            hb.strokestyle = "#212121";
            bigengineer.default.DrawRoundRect(hb, A, C, 100);
            hb.stroke();
            hb.closePath();
        },
        DrawAOBArc() {
            let cc = this.$refs.cc2;
            let hb = cc.getContext("2d");

            let A = new Array(5, 5);
            let O = new Array(130, 130);
            let C = new Array(5, 150);

            hb.beginPath();
            hb.strokestyle = "#212121";
            bigengineer.default.DrawAOBArc(hb, A, O, C, 10);
            hb.stroke();
            hb.closePath();
        },
        DrawQuadraticCurveTo() {
            let cc = this.$refs.cc3;
            let hb = cc.getContext("2d");

            let A = new Array(5, 5);
            let O = new Array(130, 130);
            let C = new Array(5, 150);

            hb.beginPath();
            hb.strokestyle = "#212121";
            bigengineer.default.DrawQuadraticCurveTo(hb, A, O, C);
            hb.stroke();
            hb.closePath();
        },
        // 贝塞尔曲线
        DrawbezierCurveTo() {
            let cc = this.$refs.cc4;
            let hb = cc.getContext("2d");

            let A = new Array(50, 50);
            let O1 = new Array(90, 30);
            let O2 = new Array(110, 35);
            let B = new Array(150, 50);
            hb.beginPath();
            hb.strokestyle = "#212121";
            bigengineer.default.DrawbezierCurveTo(hb, A, O1, O2, B);
            hb.stroke();
            hb.closePath();
        },
        // 弧线
        DrawArc() {
            let cc = this.$refs.cc5;
            let hb = cc.getContext("2d");
            let B = new Array(100, 100);
            hb.beginPath();
            hb.strokestyle = "#212121";
            bigengineer.default.DrawArc(hb, B, 49, 0,-90, true);
            hb.stroke();
            hb.closePath();
        }
    },
    watch: {},
    filters: {}
};
</script>
 
<style></style>
 