<template>
    <div class="logWindow">
        <h5>log</h5>
        <table class="logTable">
            <tr>
                <td class="log_id">id</td>
                <td class="log_time">time</td>
                <td class="log_topic">topic</td>
                <td class="log_message">message</td>
            </tr>
            <tr v-for="item in logContent">
                <td class="log_id">unsupported</td>
                <td class="log_time">unsupported</td>
                <td class="log_topic">{{item.key}}</td>
                <td class="log_message">{{item.message}}</td>
            </tr>
        </table>
    </div>
</template>
<script>
export default{
    props: {
        logContent: Object(),
    }
}
</script>
<style>
    .logWindow{
        background-color: aliceblue;
        width: 70%;
        margin: 20pt;
    }
    .logTable{
        background-color: antiquewhite;
    }
    .log_id{
        width: 20pt;
    }
    .log_time{
        width: 100pt;
    }
    .log_topic{
        width: 400pt;
    }
    .log_message{
        width: 500pt;
    }
</style>