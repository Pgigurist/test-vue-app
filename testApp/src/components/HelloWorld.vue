<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>{{text}}</p>
    <!--input type="text" v-model='text'-->
    <!--input type="submit" @click='onSubmit'-->
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
        msg: 'Welcome to Your Vue.js App',
        text:   'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nobis numquam rem eveniet facilis nam! Magnam rerum '
    }
  },
    methods: {
    
            onSubmit : function(){
                this.text = 'submit'
            }
    
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
