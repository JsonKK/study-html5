<template>
    <div id></div>
</template>
 
<script>
export default {
    name: '',
    props: {},
    components: {},
    data() {
        return {}
    },
    mounted() { 
        console.log(typeof postMessage);
        window.addEventListener("message", (event)=>{
            let e = event;
            if(e){
                console.error(e.data);
            }
            
        }, false);
        parent.postMessage('welcome child', '*');
    },
    computed: {},
    methods: {},
    watch: {},
    filters: {}
}
</script>
 
<style></style>
 