<script setup>
import Card from "./Card.vue"
const onClickAdd=()=>{
  alert(111)
}
</script>

<template>
<div class="p-10">
    
    <h2 class="text-3xl font-bold mb-8">Все кроссовки</h2>
      <div class="grid grid-cols-4 gap-5">
        <Card 
        title="Кроссовки мужские Nike xxx" 
        img-url="/sneakers/sneakers-1.jpg" 
        :price="5000"
        :onClickAdd="onClickAdd"
        />
        <Card/>
        <Card/>
        <Card/>
        <Card/>
      </div>
    
  </div>
</template>
