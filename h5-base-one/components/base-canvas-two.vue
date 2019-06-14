<template>
    <div id>
        <canvas ref="diagonal" style="border:1px solid;" :width="width" :height="height"></canvas>
    </div>
</template>
 
<script>
export default {
    name: "",
    props: {},
    components: {},
    data() {
        return {
            width: 400,
            height: 500
        };
    },
    mounted() {
        this.initCanvas();
        this.drawTrail();
    },
    computed: {},
    methods: {
        initCanvas() {
            let canvas = this.$refs.diagonal;
            let context = canvas.getContext("2d");

            context.save();

            context.translate(100, 100);

            context.beginPath();
            context.moveTo(0, 0);
            context.lineTo(0, -100);
            context.stroke();

            context.restore();
        },
        drawTrail() {
            let canvas = this.$refs.diagonal;
            let context = canvas.getContext("2d");
            context.save();
            context.clearRect(0, 0, this.width, this.height);
            context.translate(130, 250);
            context.save();
            context.transform(1, 0, -0.5, 1, 0, 0);
            context.scale(1, 0.6);
            
            this.createCanopyPath(context, 2);
            context.restore();
            this.createCanopyPath(context);
            context.restore();

            //绘制小路
            context.save();
            context.translate(-10, 350);
            context.beginPath();
            context.moveTo(0, 0);
            context.quadraticCurveTo(170, -50, 260, -190);
            context.quadraticCurveTo(310, -250, 410, -250);
            context.strokeStyle = "#663300";
            context.lineWidth = 20;
            context.stroke();
            context.restore();

            //绘制第二颗树
            context.save();
            context.translate(260, 500);
            context.scale(2, 2);
            this.createCanopyPath(context);
            context.stroke();
            // context.restore();
            context.transform(1, 0, -0.5, 1, 0, 0);
            context.scale(1, 0.6);
            this.createCanopyPath(context, 2);
            context.restore();

            context.save();
            context.font = "60px impact";
            context.fillStyle = "#996600";
            context.textAlign = "center";
            context.shadowBlur=10;
            context.shadowColor = 'rgba(0,0,0,0.2)';
            context.shadowOffsetX = 15;
            context.fillText('happy trails',200,60,400);
            context.restore();
        },
        createCanopyPath(context, type) {
            if (!context) {
                return;
            }
            context.lineWidth = 4;
            context.lineJoin = "round";
            context.beginPath();
            context.moveTo(-25, -50);
            context.lineTo(-10, -80);
            context.lineTo(-20, -80);
            context.lineTo(-5, -110);
            context.lineTo(-15, -110);

            context.lineTo(0, -140);

            context.lineTo(15, -110);
            context.lineTo(5, -110);
            context.lineTo(20, -80);
            context.lineTo(10, -80);
            context.lineTo(25, -50);

            context.closePath();

            if (type == 2) {
                context.strokeStyle = "rgba(0,0,0,0.1)";
                context.stroke();
                context.fillStyle = "rgba(0,0,0,0.1)";
                context.fillRect(-5, -50, 10, 50);
                context.fill();
            } else {
                //给树干设置渐变色
                let trunkGradient = context.createLinearGradient(-5,-50,5,-50);
                trunkGradient.addColorStop(0, "#663300");
                trunkGradient.addColorStop(0.4, "#996600");
                trunkGradient.addColorStop(1, "#552200");
                // context.fillStyle = "#663300";
                context.fillStyle = trunkGradient;
                context.fillRect(-5, -50, 10, 50);
                let canopyShadow = context.createLinearGradient(0, -50, 0, 0);
                canopyShadow.addColorStop(0, "rgba(0,0,0,0.5)");
                canopyShadow.addColorStop(0.2, "rgba(0,0,0,0.0)");
                context.fillStyle = canopyShadow;
                context.fillRect(-5, -50, 10, 50);

                context.strokeStyle = "#663300";
                context.stroke();
                context.fillStyle = "#339900";
                context.fill();
            }
        }
    },
    watch: {},
    filters: {}
};
</script>
 
<style></style>
 