<template>
    <div class="infoPanel">
        <h4>Info</h4>
        <table clsss="statusTable">
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
        <div class="upload">
            add file
        </div>
        <div class="btnPanel">
            <div class="startBtn" v-on:click="startAct">start</div>
            <div class="pauseBtn" v-on:click="pauseAct">pause</div>
            <div class="delBtn" v-on:click="delAct">del</div>
        </div>
    </div>
</template>
<script>
export default{
    data: function(){
        return{
   
        }
    },
    methods:    {
        startAct:   function(){
            alert('start '+this.infoData.key)  
        },
        pauseAct:   function(){
            alert('pause '+this.infoData.key)  
        },
        delAct:     function(){
            alert('del '+this.infoData.key)  
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
        width: 350pt;
        height: 177pt;
        background-color: #ffffff;
        border: 3pt solid #b8ecb8;
        border-radius: 10pt;
    }
    table{
        margin: 10pt;
        width: 40%;
        float: left;
    }
    .upload{
        border: 1pt dashed #c7c7c770;
        border-radius: 5pt;
        margin: 10pt;
        float: right;
        width: 35%;
        height: 33%;
        
    }
    .btnPanel{
        padding-left: 8pt;
        
    }
    .btnPanel div{
        border: 1pt solid #c7c7c770;
        float: left;
        width: 100pt;
        margin: 5pt;
        border-radius: 3pt;
        background-color: #c7c7c770;
    }
    .startBtn:hover{
        background-color: #5df9548f;
    }
    .pauseBtn:hover{
        background-color: #c7e86699;
    }
    .delBtn:hover{
        background-color: #e8666699;
    }
</style>