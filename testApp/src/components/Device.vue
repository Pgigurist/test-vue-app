<template>
    <div class="device" v-bind:class="">{{device.data}}</div>
</template>

<script>

export default{
    
    
    data: function(){
      return{
          status: false
      }  
    },
    props:{
        device: Object
    }
}
</script>
<style>
    .device{
        width: 200pt;
        background-color: aliceblue;
    }
</style>