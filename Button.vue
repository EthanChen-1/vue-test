<template>
    <button @click="onClick()" v-bind:style="{background: color}"> {{text}} </button>
</template>

<script>
    export default{
        name: 'Button',
        props:{
            text: String,
            color: String,
        },
        methods:{
            onClick(){
                this.$emit('btn-click');
            }
        }
    }
</script>

<style scoped>
    button{
        width:100px;
        height: 50px;
        border-radius: .5em;
        color:white
    }
</style>