<script setup>
import { onMounted, reactive, ref, watch } from "vue";
import Headep from "./components/Headep.vue"
import CardList from "./components/CardList.vue"
import Drawer from "./components/Drawer.vue"

import axios from "axios";

const items = ref([])

const filters = reactive({
sortBy:'title',
searchQuery:'',
})


const onChangeSelect=(event)=>{
  filters.sortBy=event.target.value;
}

const onChangeSearchInput = (event)=>{
  filters.searchQuery=event.target.value
}

const fetchItems = async () => {
  try {
    const params ={
      sortBy: filters.sortBy,
    }

if (filters.searchQuery){
  params.title=`*${filters.searchQuery}*`
}

  const{data}=await axios.get(`https://604781a0efa572c1.mokky.dev/items`, 
  {
    params
  }
  )
  items.value=data
} catch (err){
  console.log(err)
}
}

onMounted(fetchItems)

watch(filters, fetchItems);

</script>

<template>
  <!--<Drawer/>-->
  <div
    class="bg-white w-4/5 m-auto rounded-xl shadow-xl mt-14"
  >
  <Headep/>

  <div class="p-10">
    <div class="flex justify-between items-center">
      <h2 class="text-3xl font-bold mb-8">Все кроссовки</h2>

      <div class="flex gap-4">
      <select @change="onChangeSelect" class="py-2 px-3 border rounded-md outline-none">
        <option value="name">По названию</option>
        <option value="price">Сначала дешевые</option>
        <option value="-price">Сначала дорогие</option>
      </select>
      <div class="relative">
        <img
          class="absolute left-3 top-3"
          src="/search.svg"
        />
        <input 
        @input="onChangeSearchInput"
        class="border rounded-md py-2 pl-10 pr-4 outline-none focus:border-gray-400" 
        placeholder="Поиск"/>
      </div>
      </div>

    </div>
  </div>

  <div class="mt-10">
    <CardList :items="items"/>
  </div>

  </div>
</template>

<style scoped>

</style>
