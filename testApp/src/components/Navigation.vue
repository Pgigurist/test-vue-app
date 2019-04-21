<template>
    <div class="navDiv">
        test
        <div class="navBtnPanel">
            <button v-on:click="sendTopicStatus">topics status</button>
            <button v-on:click="sendMessageLog">message log</button>
        </div>
    </div>
</template>
<script>
export default{
    data:   function(){return{

        }
    },
    methods:    {
        sendTopicStatus: function(){
            this.$emit('showstatus', null)
            console.log('emit status')
        },
        sendMessageLog: function(){
            this.$emit('showlog', null)
            console.log('emit log')
        }
    }
}
</script>
<style>
    .navDiv{
        height: 50pt;
        width: 100%;
        background-color: #c7c7c7;
    }
    .navBtnPanel{
        
    }
    .navBtnPanel button{
        height: 30pt;
        width: 100pt;
        font-size: 10pt;
        border-radius: 10pt;
        background-color: darkseagreen;
    }
</style>
