<template>
    <div id="">
        <section>
            <table>
                <template v-for="(item,index) in list">
                    <template v-if="(index+1)%3==1">
                        <tr :key="index">
                            <td @mouseover="initHover">{{item}}</td>
                            <td @mouseover="initHover" v-if="list[index+1]">{{list[index+1]}}</td>
                            <td @mouseover="initHover" v-if="list[index+2]">{{list[index+2]}}</td>
                        </tr>
                    </template>
                </template>
            </table>
            <div>Focus the button,hover over the table cells, and Hit Enter to identify them using querySelector('td:hover')</div>
            <button type="button" id="findHover" autofocus>Find 'td:hover' targer</button>
            <div id="hoverResult">{{msg}}</div>
        </section>
    </div>
</template>
 
<script>
    export default {
        name: '',
        props:{},
        components: {},
        data(){
            return {
                list:['A1','A2','A3','B1','B2','B3','C1','C2','C3','D1','D2','D3','E1','E2','E3'],
                msg:''
            }
        },
        mounted(){
            this.initHover()
        },
        computed:{},
        methods:{
            initHover(e){
                // let hoverd = document.querySelector('td:hover');
                if(e){
                    this.msg = e.currentTarget.innerHTML;
                }
            }
        },
        watch:{},
        filters:{}
    }
</script>
 
<style>
td{
    border-style: solid;
    border-width: 1px;
    font-size: 300%;
}
td:hover{
    background: cyan;
    cursor: default;
}
#hoverResult{
    color: green;
    font-size: 200%;
}
</style>
 