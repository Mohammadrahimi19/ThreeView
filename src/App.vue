<script setup>
import { reactive } from 'vue';
import Home from './components/Home.vue';
const items = reactive(
  
  {
    name:"username",
    nodes:[
      {
      
        name:"mohammad1",
        nodes:[{
          name:"mohammad1.1",
          nodes:[]
          
        }]
      },
      {
      
        name:'mohammad2',
        nodes:[]
        
      }
    ]
  },

)

</script>

<template>
  <Home :item="items" />
</template>

<style >

</style>