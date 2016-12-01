<template>
  <div class="hello">

    <h1 v-text="message"></h1>
    <span v-once>This will never change: {{message}}</span>
    <div v-html="rawHTML"></div>
    <h1 v-if="ifShow" v-on:click="show"> V-if </h1>
    <h1 v-else v-on:click="show"> v-else </h1>
    <h1 v-show="ifShow" > V-show  </h1>
    <input v-model="newMsg" @keyup.enter="onEnter">
    <button v-on:click="say('hello!', $event)">Submit</button>
    <h1 v-for= "item in items">{{item.name}}</h1>
    <div v-bind:class="classA">v-bind</div>
    <span > V-pre {{ message }}</span><br/>
    <span v-pre> V-pre {{ message }} </span>
    <div v-cloak> {{ message }} </div>


  </div>
</template>

<script>
export default {
  name: 'hello',
  data: function () {
    return{
      message: 'Welcome to Owen Vue.js App (V-text)',
      rawHTML: '<h2> This is HTML (V-html)</h2>',
      ifShow:false,
      newMsg: '',
      items:[
      {name: 'Owen', Sex: 'Male',tech:'v-for'},
      {name: 'Owen2', Sex: 'Male',tech:'v-for'}
      ],
      classA: 'classA'     
      
    }
  },

  methods:{
      show:function(){
        this.ifShow = !this.ifShow;
      },
      onEnter:function(){
        this.message = this.newMsg;
        this.newMsg = '';
      },
      say: function (msg, event) {
        console.log(event);
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

.classA{
 font-size: 50px;
 color: red;
}

[v-cloak] {
  display: none;
  font-size:100px;
}

</style>
