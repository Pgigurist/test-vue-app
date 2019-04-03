<template>
   
    <li class="node-tree">
        <div class="label" v-bind:class="{connected: node.status, disconnected: !node.status}">
            <h4>{{node.data}}</h4>
            <p>{{status}}</p>
            <div class="bPanel">
                <button class="showButton" v-on:click="show = !show">SHOW</button>
                <button class="delButton" v-on:click="del()">DEL</button>
            </div>
        </div>
        
           
        <transition>
           <div v-if="show">
                <ul v-if="node.children && node.children.length">
                    <node v-for="child in node.children" :node="child" :key="child.key"></node>
                </ul>
            </div>
        </transition>
    </li>
</template>
 

<script>

    import Device from './../Device.vue'

    export default{
        
        data: function(){return{
            status: false,
            show: false
        }},
        methods:{
            del: function(){
                alert('комманда удалить '+this.node.data)
            }
        },
        name: "node",
        props: {
            node: Object,
            //device: Object
            //key: String
        }
    }
</script>

<style>
    .label{
        width: 200pt;
        height: 50pt;
        border-radius: 7pt;
    }
    .connected{
        background-color: #b8ecb8
    }
    .disconnected{
        background-color: #f99b9b
    }
    
    .bPanel{
        position: relative;
        top: -61pt;
        left: 140pt;
        width: 60pt;
        height: 50pt;
    }
    
    .label .showButton{
        width: 60pt;
        height: 25pt;
        border-radius: 0 7pt 0 0;
        background-color: #b8ecb8;
        
    }
    
    .label .delButton{
        width: 60pt;
        height: 25pt;
        border-radius: 0 0 7pt 0;
        background-color: #dc9d86;
    }
</style>