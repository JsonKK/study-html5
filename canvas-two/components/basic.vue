<template>
    <div id="basic">
        <h1>basic</h1>
        <canvas id="canvas" ref="canvas" width="600" height="300"></canvas>
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
        this.renderFont();
    },
    computed: {},
    methods: {
        // 渲染文字
        renderFont(){
            let canvas = this.$refs.canvas,
                context = canvas.getContext('2d');
            context.font = '38pt Arial';
            context.fillStyle = 'cornflowerblue';
            context.strokeStyle = 'blue';
            //后两个参数是横纵坐标的位置（x，y）
            //x代表的是内容的左侧
            //y代表的是内容的底部
            context.fillText('Hello Canvas',canvas.width/2 - 150,canvas.height/2 + 14);
            context.strokeText('Hello Canvas',canvas.width/2 - 150,canvas.height/2 + 14);

        }
    },
    watch: {},
    filters: {}
};
</script>
 
<style scoped>
#basic{
    background-color: #ddd;
}
#basic>h1{
    line-height: 2em;
}
#canvas{
    margin: 10px;
    padding: 10px;
    background-color: #fff;
    border: thin inset #aaa;
}
</style>
 