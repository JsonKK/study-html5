<template>
    <div id>
        <canvas
            @mousemove="canvasMove"
            id="heatMap"
            ref="heatMap"
            width="300"
            height="300"
            style="border:1px solid;"
        ></canvas>
        <button @click="reset">重置</button>
    </div>
</template>
 
<script>
export default {
    name: '',
    props: {},
    components: {},
    data() {
        return {
            context: '',
            points: {},
            scale: 3,
            x: -1,
            y: -1
        };
    },
    mounted() {
        this.initDemo();
    },
    computed: {},
    methods: {
        reset() {
            let context = this.context;
            if (context) {
                context.clearRect(0, 0, 300, 300);
            }
            this.points = {};
            this.x = -1;
            this.y = -1;
        },
        initDemo() {
            let canvas = this.$refs.heatMap,
                context = canvas.getContext('2d');
            context.globalAlpha = 0.2;
            context.globalCompositeOperation = 'lighter';
            this.context = context;
            this.sample();
        },
        sample() {
            let { x, y } = this;
            if (x != -1) {
                this.addToPoint(x, y);
            }
            setTimeout(this.sample, 100);
        },
        canvasMove(e) {
            this.x = e.pageX - e.target.offsetLeft;
            this.y = e.pageY - e.target.offsetTop;
            this.addToPoint(this.x, this.y);
        },
        getColor(instensity) {
            let colors = ['#072933', '#2E4045', '#8C593B', '#B2814E', '#FAC268', '#FAD237']
            return colors[Math.floor(instensity / 2)]
        },
        drawPoint(x, y, radius) {
            let context = this.context;
            if (context) {
                context.fillStyle = this.getColor(radius)
                radius = Math.sqrt(radius) * 10
                context.beginPath()
                context.arc(x, y, radius, 0, Math.PI * 2, true)
                context.closePath()
                context.fill()
            }
        },
        addToPoint(x, y) {
            let { scale, points } = this;
            // x = Math.floor(x / scale);
            // y = Math.floor(y / scale);

            if (!points[[x, y]]) {
                points[[x, y]] = 1
            }
            else if (points[[x, y]] == 10) {
                return;
            }
            else {
                points[[x, y]]++;
            }
            this.x = x;
            this.y = y;
            this.drawPoint(x, y, points[[x, y]]);

        }
    },
    watch: {},
    filters: {}
};
</script>
 
<style>
* {
    margin: 0;
    padding: 0;
}
body {
    text-align: center;
}
#heatMap {
    border: 1px solid;
    margin-top: 56px;
    background: url("https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1537600463&di=e982aba201c96e0bf5b26f654e5e4097&imgtype=jpg&er=1&src=http%3A%2F%2Fattachments.gfan.com%2Fforum%2F201605%2F31%2F234941i5wc5mii0juw3iat.jpg")
        no-repeat;
    background-size: 100% 100%;
}
</style>
 