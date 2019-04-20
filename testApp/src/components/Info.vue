<template>
    <div class="infoPanel">
        <h4>Info</h4>
        <table>
            <tr>
                <td>device</td>
                <td>{{infoData.device}}</td>
            </tr>
            <tr>
                <td>status</td>
                <td>{{infoData.status}}</td>
            </tr>
            <tr>
                <td>last action</td>
                <td>{{infoData.lastAction}}</td>
            </tr>
        </table>
    </div>
</template>
<script>
export default{
    data: function(){
        return{
   
        }
    },
    
    props:   {
        infoData: Object
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
        background-color: #ffffff;
        border: 3pt solid #b8ecb8;
        border-radius: 10pt;
    }
    
</style>