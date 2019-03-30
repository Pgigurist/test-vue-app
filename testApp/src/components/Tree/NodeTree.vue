<template>
    <li class="node-tree">
        <span class="label">{{node.data}}</span>
        
        <ul v-if="node.children && node.children.length">
            <node v-for="child in node.children" :node="child" :key="node.key"></node>
        </ul>
    </li>
</template>
 

<script>
    export default{
        name: "node",
        props: {
            node: Object
        }
    }
</script>