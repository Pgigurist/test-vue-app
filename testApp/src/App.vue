<template>
  <div id="app">
    <!--img src="./assets/logo.png"-->
    <!--user/-->
    <tree :tree-data="tree"></tree>
    <!--router-view/-->
  </div>
</template>

<script>

import user from './components/User.vue'
import Tree from './components/Tree.vue'
import axios from 'axios'
//import axios from 'axios'

export default {
    name: 'App',
    components: {
        user,
        Tree
    },
    
    
    data: ()=>{
        return{
            tree: JSON.parse(testData)._root
        }
    },
    created: function(){
            console.log('send get')
            axios
                .get('http://localhost:3000/getCurrentTree')
                .then(res => (this.tree = JSON.parse(res)))
    }
    
}


var testData = "{\"_root\":{\"data\":\"home\",\"key\":\"home\",\"parrent\":null,\"status\":\"connected\",\"children\":[{\"data\":\"kitchen\",\"key\":\"homekitchen\",\"parrent\":\"[Circular]\",\"status\":\"connected\",\"children\":[{\"data\":\"sensor1\",\"key\":\"homekitchensensor1\",\"parrent\":\"[Circular]\",\"status\":\"connected\",\"children\":[{\"data\":\"humidity\",\"key\":\"homekitchensensor1humidity\",\"parrent\":\"[Circular]\",\"status\":\"connected\",\"children\":[]},{\"data\":\"temperature\",\"key\":\"homekitchensensor1temperature\",\"parrent\":\"[Circular]\",\"status\":\"connected\",\"children\":[]}]},{\"data\":\"light1\",\"key\":\"homekitchenlight1\",\"parrent\":\"[Circular]\",\"status\":\"disconnected\",\"children\":[{\"data\":\"state\",\"key\":\"homekitchenlight1state\",\"parrent\":\"[Circular]\",\"status\":\"disconnected\",\"children\":[]}]},{\"data\":\"sensor2\",\"key\":\"homekitchensensor2\",\"parrent\":\"[Circular]\",\"status\":\"connected\",\"children\":[{\"data\":\"light\",\"key\":\"homekitchensensor2light\",\"parrent\":\"[Circular]\",\"status\":\"connected\",\"children\":[]}]}]},{\"data\":\"livingroom\",\"key\":\"homelivingroom\",\"parrent\":\"[Circular]\",\"status\":\"connected\",\"children\":[{\"data\":\"temperature\",\"key\":\"homelivingroomtemperature\",\"parrent\":\"[Circular]\",\"status\":\"connected\",\"children\":[]}]}]}}"

const tr = {
  label: "A cool folder",
  children: [
    {
      label: "A cool sub-folder 1",
      children: [
        { label: "A cool sub-sub-folder 1" },
        { label: "A cool sub-sub-folder 2" }
      ]
    },
    { label: "This one is not that cool" }
  ]
}

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
