<template>
    <form action="#">
        <datalist id="cars">
            <option value="BMW"></option>
            <option value="Ford"></option>
            <option value="Volvo"></option>
        </datalist>
        <input type="text"  id="content" list="cars"/>
        <input type="text" required/>
    </form>
</template>
 
<script>
export default {
    name: '',
    props: {},
    components: {},
    data() { return {} },
    mounted() { },
    computed: {},
    methods: {},
    watch: {},
    filters: {}
}
</script>
 
<style></style>
 