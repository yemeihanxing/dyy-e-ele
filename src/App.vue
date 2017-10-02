<template>
  <div id="app">
    <v-header :seller="seller"></v-header>
  </div>
</template>

<script>
  import axios from 'axios';
  import header from './components/header/header';
export default {
  name: 'app',
  data(){
    return {
      seller:{}
    }
  },
  created(){
    const Super = this;
    axios.get('/api/seller').then(function (response) {
      Super.seller = response.data.data;
      console.log('response:',response.data.data);
    }).catch((error)=>{
      console.log('error:',error);
    })
  },
  components:{
    'v-header': header
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
