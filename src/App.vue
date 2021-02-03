<template>
  <div id="app">
    <h1>Invoice App</h1>
     <!-- //<b-button class="btn" variant="outline-primary">Create Invoice +</b-button> -->
     <!-- <HelloWorld v-on:onSubmit="onSubmit"/> -->
    
     <Table />
  </div>
</template>

<script>

import Table from './components/Table.vue';
// import HelloWorld from './components/HelloWorld.vue';

export default {
  name: 'App',
  components: {
    Table,
    //HelloWorld
  } ,
  methods:{
    
  }
}
</script>

<style>
#app {
  background-color: #2c3e50;
  
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #fff;
  margin-top: 60px;
}

.btn{
  margin: 50px;
  
}
</style>
