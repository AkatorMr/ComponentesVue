<template>
    <div class="tree-node">
        <span>{{nombre}}</span>
        <slot>No</slot>
    </div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
    name:"tree-node",
    props:{
        nombre:String
    },
    data:function(){
        return({

        });
    },
    methods:{

    },
    mounted:function(){

    }
})
</script>
<style  scoped>
    .tree-node{
        padding-left:20px;
    }
    .tree-node::before{
        content: "";
        width: 20px;
        height: 100%;
        background-color: blue;
    }
</style>