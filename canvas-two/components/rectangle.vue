<template>
    <div id>
        <canvas @click="clearCanvas" ref="canvas" width="600" height="400"></canvas>
    </div>
</template>
 
<script>
export default {
    name: "",
    props: {},
    components: {},
    data() {
        return {};
    },
    mounted() {
        this.render();
    },
    computed: {},
    methods: {
        render(){
            let canvas = this.$refs.canvas,
                context = canvas.getContext('2d'),
                gradient = context.createLinearGradient(0,0,canvas.width,0);
            context.font = '20px Helvetica';
            gradient.addColorStop(0,'cadetblue');
            gradient.addColorStop(0.25,'blue');
            gradient.addColorStop(0.5,'chocolate');
            gradient.addColorStop(1,'cadetblue');
            context.lineJoin = 'round';
            context.lineWidth = 30;
            context.fillStyle = gradient;
            // context.strokeText('click everyWhere to erase',175,200);
            context.fillText('click everyWhere to erase',175,200);
            //样式
            context.strokeStyle = 'goldenrod';
            context.fillStyle = 'rgba(0,0,255,0.5)';
            //x:左侧距离，y距离上部距离
            context.strokeRect(30,100,200,200);
            context.fillRect(325,100,200,200);
        },
        clearCanvas(){
            let canvas = this.$refs.canvas,
                context = canvas.getContext('2d');
            // context.clearRect(0,0,canvas.width,canvas.height);
            context.clearRect(325,100,200,200);
        }
    },
    watch: {},
    filters: {}
};
</script>
 
<style></style>
 