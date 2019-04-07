<template>
    <div class="infoPanel">
        <h4>Info</h4>
    </div>
</template>
<script>
export default{
    data: function(){
        return{
            name:   '',
            key:    '',
            status: '',
            message:'',
        }
    }
}
</script>
<style>
    .infoPanel{
        margin: 10pt;
        position: fixed;
        left: 60%;
        width: 35%;
        height: 60%;
        background-color: #e9f187;
        border-radius: 10pt;
    }
    
</style>