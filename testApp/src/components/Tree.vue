<template>
    <div class="tree">
        <ul class="tree-list">
            <node-tree :node="treeData"></node-tree>
        </ul>
    </div>
</template>

<script>
    //import axios from 'axios'
    import NodeTree from './Tree/NodeTree'

    export default {
        
        props:  {
            treeData: Object
        },
        components: {
            NodeTree
        }
        
    }
</script>


<style>
    .tree-list ul{
        padding-left: 36px;
        margin: 6px 0;
        list-style-type: none;
    }
</style>