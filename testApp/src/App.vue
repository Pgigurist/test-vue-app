<template>
  <div id="app">
    <!--img src="./assets/logo.png"-->
    <!--user/-->
    <navigation @showstatus="showstatus" @showlog="showlog"/>
    <transition>
        <div class="topicStatus" v-if="topicStatus">
            <info :info-data="info"/>
            <tree :tree-data="tree" @del="del" @info="setInfo"></tree>
        </div>
        <div v-if="logData">
            <log :logContent="log"/>
        </div>
    </transition>
    
    <!--router-view/-->
  </div>
</template>

<script>

import user from './components/User.vue'//rm in future
import Tree from './components/Tree.vue'
import axios from 'axios'
import Navigation from './components/Navigation.vue'
import Info from './components/Info.vue'
import log from './components/log.vue'

export default {
    name: 'App',
    components: {
        Navigation,
        Info,
        user,
        Tree,
        log,
    },
    
    
    data: ()=>{
        return{
            tree: null,
            ws: null,
            loading: false,
            topicStatus: true,
            logData:   false,
            log: [],
            info: {
                device: 'unkmown',
                status: false,
                lastAction: 'uncknown'
            }
        }
    },
    ///*
    methods: {
      getTree: function(){
          this.loading = true
          axios.get('api/getCurrentTree/', { crossdomain: true })
            .then((response)=>{
                this.loading = false
                //console.log(response.data)
                this.tree = JSON.parse(response.data)._root
            }, (err)=>{
              this.loading = false
          })
      },
      search: function(key, callback, elm){
          //console.log('Search: '+key)
          if(elm == undefined){
              elm = this.tree
          }
          if(elm.key == key){
              
              callback(elm)
          }else{
              for(var i=0; i<elm.children.length; i++){
                  this.search(key ,callback ,elm.children[i])
              }
          }
      },
        del:    function(pkg){
            if(confirm('комманда удалить '+pkg.data)){
                //console.log('recent: ')
                let data = {
                    message: 'remove',
                    node:    pkg
                }
                console.log(data)
                this.ws.send(JSON.stringify(data))
                this.getTree()
            }
        },
        setInfo:   function(pkg){
            //console.log('info '+pkg)
            //info.methods.setData(pkg)
            this.info.device = pkg.data
            this.info.status = pkg.status
            console.log('key is: '+pkg.key)
            this.info.lastAction = this.getLastMessage(pkg.key)
        },
        showstatus:    function(data){
            this.topicStatus = true
            this.logData = false
        },
        showlog: function(data){
            this.topicStatus = false
            this.logData = true
        },
        addLogContent:  function(data){ 
            this.log.push(data)
        },
        getLastMessage: function(key){
            let index =0;
            for(var i=0; i<log.length; i++){
                let currentKey = log[i].key.split('/').join('')
                if(currentKey == key){
                    index = i
                }
            }
            if(index == 0){
                return 0
            }else{
                return log[i]
            }
        }
    },
    
    beforeMount: function(){
            this.getTree()
    },
    created: function(){
        
        var self = this
        this.ws = new WebSocket('ws://localhost:40510')
        this.ws.onopen = ()=>{
            console.log('ws connected')
        }
        this.ws.onclose = (eventclose)=>{
            console.log('соединение закрыто причина: '+eventclose)
        }
        this.ws.onmessage = (mes)=>{
            
            var data = JSON.parse(mes.data)
            
            this.addLogContent(data)
            
            switch(data.message){
                case 'connected':
                    this.search(data.key, (elm)=>{
                        elm.status = true
                    })
                    break
                case 'disconnected':
                    //do nothing
                    this.search(data.key, (elm)=>{
                        elm.status = false
                    })
                    break
                default:
                    //do nothing
                    //this.search(data.key, (elm)=>{
                    //    elm.action = false
                    //})
                    break
            }
            
            
            
            //this.$emit('statUpdate', msg)
        }
    }
}
// CSS 

</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
