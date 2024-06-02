<script setup>
defineProps({
  imageUrl:String,
  title:String,
  price:Number,
  isFavorite:Boolean,
  isAdded:Boolean,
  onClickAdd:Function,
  onClicFavorite:Function,
})

</script>

<template>
  <div
    class="relative bg-white border border-slate-100 rounded-xl p-8 cursor-pointer transition hover:shadow-xl hover:transform hover:-translate-y-2"
  >
    
      <img 
      :src="!isFavorite ? '/like-1.svg' : '/like-2.svg'" 
      alt="Like 1" 
      class="absolute top-8 left-8" 
      @click="onClicFavorite"
      />
    
    <img :src="imageUrl" alt="Sneaker" />
    <p class="mt-2">{{ title }} </p>
    <div class="flex justify-between mt-5">
      <div class="flex flex-col gap-2">
        <span class="text-slate-400">Цена:</span>
        <span class="font-bold">{{price}}.</span>
      </div>
      <img @click="onClickAdd" :src="!isAdded ? '/plus.svg' : '/checked.svg'" alt="Plus" />
    </div>
  </div>
</template>
