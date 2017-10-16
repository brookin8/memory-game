<template>
  <div id="app">
  <h1> Memory </h1>
    <board v-on:boardClicked="catchBoard" />
  </div>
</template>

<script>
import board from './components/board.vue'


export default {
  name: 'app',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
    }
  },
  components : {
    board
  },

  props : ['cardNumb'],

  methods : {
    catchBoard : function(cardNumb) {
      alert(cardNumb)
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
  text-align: left;
  margin-left: 34%;
  font-size: 400%;
  margin-bottom: 1%;
  font-family: 'Gabriela', serif;

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
