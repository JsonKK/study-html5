<template>
    <div id="" class="out-box">
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
            lineAxex:{
                x : 0,
                y : 0
            },
            width:200,
            height:200
        };
    },
    mounted() {
        this.initCanvas();
    },
    computed: {},
    methods: {
        initCanvas(){
            let canvas = this.$refs.diagonal;
            let context = canvas.getContext('2d');
            this.context = context;
            this.moveLine();
            setInterval((res)=>{
                this.moveLine();
            },10);
        },
        moveLine(){
            let context = this.context,
                lineAxex = this.lineAxex,
                width = this.width,
                height = this.height;
            if(context && lineAxex){
                if(lineAxex.x < width && lineAxex.y == 0){
                    lineAxex.x  += 1;
                }
                if(lineAxex.x == width && lineAxex.y < height){
                    lineAxex.y  += 1;
                }
                if(lineAxex.y == 200 && lineAxex.x > 0){
                    lineAxex.x -= 1;
                }
                if(lineAxex.x == 0 && lineAxex.y > 0){
                    lineAxex.y -=1;
                }
                context.clearRect(0,0,width,height);
                // context.translate(width/2,height/2);
                context.beginPath();
                context.moveTo(width/2,height/2);
                context.lineTo(lineAxex.x,lineAxex.y);
                context.stroke();
                Object.assign(this.lineAxex,lineAxex);
            }
        }
    },
    watch: {},
    filters: {}
};
</script>
 
<style>
.out-box{
    margin: 10px;
}
</style>
 