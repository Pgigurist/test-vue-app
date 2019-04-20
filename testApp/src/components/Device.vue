<template>
    <div class="device" v-bind:class="">{{node.data}}</div>
</template>

<script>

export default{
    
    
    data: function(){
      return{
          status: false
      }  
    },
    props:{
        node: Object
    }
}
</script>
<style>
    .device{
        width: 200pt;
        background-color: aliceblue;
    }
</style>