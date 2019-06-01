<template>
    <div id>
        <div id="glasspane" ref="glasspane" @click.prevent>
            <h2 class="title">Bouncing Ball</h2>
            <p>one hunder balls bouncing</p>
            <a id="startButton" ref="startButton" @click.prevent="paused=!paused">{{paused? 'Stop' : 'Start'}}</a>
        </div>
        <canvas class="canvas" ref="canvas" width="750" height="500"></canvas>
    </div>
</template>
 
<script>
export default {
    name: "",
    props: {},
    components: {},
    data() {
        return {
            paused : false
        };
    },
    mounted() {
        this.initBall();
    },
    computed: {
        
    },
    methods: {
        initBall(){
            let context = this.$refs.canvas.getContext('2d'),
                glasspane = this.$refs.glasspane;
        }
    },
    watch: {},
    filters: {}
};
</script>
 
<style scoped>
body {
    background-color: #ddd;
}
.canvas {
    margin: 10px 0 0 10px;
    background-color: #fff;
    border: thin solid #aaa;
}
#glasspane {
    position: absolute;
    left: 50px;
    top: 50px;
    padding: 0px 20px 10px 10px;
    background: rgba(0, 0, 0, 0.3);
    border: thin solid rgba(0, 0, 0, 0.6);
    color: #eee;
    font-size: 12px;
    cursor: pointer;
    box-shadow: rgba(0, 0, 0, 0.5) 5px 5px 20px;
}
#glasspane h2 {
    font-weight: normal;
}
#glasspane .title {
    font-size: 2em;
    color: rgba(255, 255, 0, 0.8);
}
#glasspane a:hover {
    color: yellow;
}
#glasspane a {
    text-decoration: none;
    color: #ccc;
    font-size: 3.5em;
}
#glasspane p {
    margin: 10px;
    color: rgba(65, 25, 220, 1);
    font-size: 1em;
}
</style>
 