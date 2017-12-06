<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div>
    <ul>
     
    </ul>
    </div>
    <div>
        <input type="text" v-model="input_val">
    </div>
    <div>
        Input Value: <span v-text="input_val"></span>
    </div>
     <div>
      <button class="btn btn-primary" v-on:click="counter++">You've clicked this button {{counter}} times!</button>
    </div>
  </div>
  
</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      users: [
        {firstname: 'Sebastian', lastname: 'Eschweiler'},
        {firstname: 'Bill', lastname: 'Smith'},
        {firstname: 'John', lastname: 'Porter'}
    ],
    inpou_val :'',
    counter:0
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
