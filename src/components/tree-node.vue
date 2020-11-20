<template>
    <div class="tree-node">
        <div :class="folder()"></div>
        <div @click="open_tree^=true">{{nombre}}</div>
        <div class="tree-node-child" v-if="open_tree">
            <slot>No</slot>
        </div>
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
            open_tree:false
        });
    },
    methods:{
        folder:function(){
            if(this.open_tree)
            return "icon icon-folder-minus";    
            return "icon icon-folder-plus";
        }
    },
    mounted:function(){

    }
})
</script>
<style  scoped>
    .icon{
        width: 20px;
        height: 20px;
        float:left;
        background-repeat: no-repeat;
        background-size: 1rem 1rem;
        margin-right: 10px;
    }
    .icon.icon-folder-plus{
        background-image: url("./../assets/folder-plus.svg");
    }

    .icon.icon-folder-minus{
        background-image: url("./../assets/folder-minus.svg");
    }
    .tree-node div .tree-node{
        margin-left: 10px;
        padding-left:10px;
        border-left-width: 0.1rem;
        border-left-style: dashed;
        border-left-color: #acacac;
    }
   .tree-node .tree-node-child{
       margin-left: 6px;
   }
    .tree-node .span{
        
        width: 32px;
        height: 32px;
        background-color: blue;
        
    }

    
</style>