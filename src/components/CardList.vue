<script setup>
import Card from "./Card.vue"

defineProps(
  {items:Array}
)

const onClickAdd=()=>{
  alert(111)
}
</script>

<template>
<div class="p-10">
    
    
      <div class="grid grid-cols-4 gap-5">
        <Card 
        v-for="item in items"
        :key="item.id"
        :title="item.title" 
        :imageUrl="item.imageUrl" 
        :price="item.price"
        :onClickAdd="onClickAdd"
        :isAdded="true"
        />
        
      </div>
    
  </div>
</template>
