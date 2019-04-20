<template>
   
    <li class="node-tree">
        <div class="label" v-bind:class="{connected: node.status, disconnected: !node.status}">
            <h4 v-on:click="infoNode">{{node.data}}</h4>
            <!--p></p-->
            <div class="bPanel">
                <button class="showButton" v-on:click="show = !show">{{shown()}}</button>
                <button v-if="node.parrent != null" class="delButton" v-on:click="removeNode">DEL</button>
            </div>
        </div>
        <transition>
           <div v-if="show">
                <ul v-if="node.children && node.children.length">
                    <node v-for="child in node.children" :node="child" :key="child.key" @del="del" @info="info"></node>
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
            show: false,
        }},
        methods:{
            removeNode: function(){
                //
                console.log('emit del in '+this.node.data)
                this.$emit('del', this.node)
            },
            shown:  function(){
                if(this.show){
                    return 'HIDE'
                }
                return 'SHOW'
            },
            del: function(pkg){
                console.log('pass del upper')
                this.$emit('del', pkg)
            },
            infoNode: function(){
                console.log('emit info in '+this.node.data)
                this.$emit('info', this.node)
            },
            info:   function(pkg){
                console.log('pass info upper')
                this.$emit('info', pkg)
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
    .label h4 {
        padding-top: 15pt;
    }
    
    .label p{
        color:aliceblue;
    }
    .bPanel{
        position: relative;
        top: -47pt;
        left: 140pt;
        width: 60pt;
        height: 48pt;
    }
    
    .label .showButton{
        width: 60pt;
        height: 25.5pt;
        border-radius: 0 7pt 0 0;
        background-color: #b8ecb8;
        
    }
    
    .label .delButton{
        width: 60pt;
        height: 24pt;
        border-radius: 0 0 7pt 0;
        background-color: #dc9d86;
    }
    
    
</style>