<template>
    <div id="clock">
        <canvas id="canvas" ref="canvas" width="300" height="300"></canvas>
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
        this.renderClock();
        this.eventClock();
    },
    computed: {},
    methods: {
        eventClock(){
            let canvas = this.$refs.canvas;
            canvas.addEventListener('mousedown',function(e){
                let v = e;
            });
        },
        renderClock(){
            let canvas = this.$refs.canvas,
                context = canvas.getContext('2d'),
                font_height = 15,
                margin = 35,
                hand_truncation = canvas.width/25,
                hourt_hand_truncation = canvas.width/10,
                number_space = 10,
                radius = canvas.width/2-margin,
                hand_radius = radius + number_space;

            function drawCircle(){
                context.beginPath();
                context.arc(canvas.width/2,canvas.height/2,radius,0,Math.PI*2,true);
                context.stroke();
            }

            function drawNumerals(){
                let numerals = [1,2,3,4,5,6,7,8,9,10,11,12],
                    angle = 0,
                    numeralWidth = 0;
                numerals.forEach((ele)=>{
                    angle = Math.PI/6 * (ele - 3);
                    numeralWidth = context.measureText(ele).width;
                    context.fillText(ele,canvas.width/2 + Math.cos(angle)*hand_radius - numeralWidth/2,
                    canvas.height/2 + Math.sin(angle)*(hand_radius) + font_height/3);
                });
            }

            function drawCenter(){
                context.beginPath();
                context.arc(canvas.width/2,canvas.height/2,5,0,Math.PI*2,true);
                context.stroke();
            }

            function drawHand(loc,isHour){
                let angle = (Math.PI*2) * (loc/60) - Math.PI/2,
                    handRaius = isHour ? radius - hand_truncation - hourt_hand_truncation : radius - hand_truncation;
                context.moveTo(canvas.width/2,canvas.height/2);
                context.lineTo(canvas.width/2 + Math.cos(angle)*handRaius,canvas.height/2 + Math.sin(angle)*handRaius);
                context.stroke();
            }

            function drawHands(){
                let date = new Date(),
                    hour = date.getHours();
                hour = hour > 12 ? hour - 12 : hour;
                drawHand(hour*5 + (date.getMinutes()/60)*5,true,0.5);
                drawHand(date.getMinutes(),false,0.5);
                drawHand(date.getSeconds(),false,0.2);

            }

            function drawClock(){
                context.clearRect(0,0,canvas.width,canvas.height);
                drawCircle();
                drawCenter();
                drawHands();
                drawNumerals();
            }
            
            context.font = font_height + 'px Arial';
            let loop = setInterval(drawClock,1000);
            
        }
    },
    watch: {},
    filters: {}
};
</script>
 
<style></style>
 