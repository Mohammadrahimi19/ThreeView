<template>
  
<div class="ml-5 " >
   <div ref="item.name" class="parent">
       <span @click="click = !click" :class="click? 'fas fa-minus':'fas fa-plus'" v-if="props.item.nodes.length"></span>
       <label :style="click?'color:red;' : 'color:black;'" for="item.name">{{ item.name }}</label>
       <div> 
        <button class="p-2  text-white bg-blue-500 rounded-xl" @click="addEvent = !addEvent" >{{ addEvent? 'cancel' : 'add' }}</button>
       </div>
   </div>
   <div v-if="addEvent" class=" parent ">
       <input @click="click = !click" type="checkbox"> 
       <input class="rounded-md   indent-2  h-fit" type="text" v-model="newChild" placeholder="New item">
       <div>
        <button  class="px-5 py-2 bg-blue-500 rounded-xl" @click="addchild">add</button>
       </div> 
   </div>


   <div v-if="props.item.nodes && props.item.nodes.length">
       <Home  class="child"
        v-show="click"
           v-for="child in props.item.nodes" 
           :key="child"
           :item="child" />
   </div>





</div>
  
</template>

<script setup>
import Home from '@/components/Home.vue'
import { defineProps,ref,} from 'vue'

let click = ref(false)
let newChild = ref('')
let addEvent = ref(false)


const props = defineProps({
    item:{
        type: Object,
        required:true
    }
})


const addchild = ()=>{
    if(newChild.value.trim()){
        if(!props.item.nodes){
            props.item.nodes = []
        }
        console.log(newChild.value);
        props.item.nodes.push({name:newChild.value , nodes:[]})
        newChild.value = ''
        addEvent.value = false
        console.log(props.item.nodes);
    }
}




</script>

<style scoped>

 .parent{
    display: flex;
    gap:4px;
    align-items: center;
    background-color: rgba(112, 128, 144, 0.678);
    width: fit-content;
    border-radius: 5px;
    padding: 5px;
    border-left: 2px solid red;
    border-right: 2px solid red;
 }
 .child{
    border-left: 2px solid silver;
    padding-left: 10px;
    margin-bottom : 2px;
    margin-top: 10px;
 }
</style>
