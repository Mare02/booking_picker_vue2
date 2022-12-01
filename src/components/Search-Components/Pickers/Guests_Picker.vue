<template>
  <div class="flex flex-col gap-5">
    <div v-for="opt in options" :key="opt.id" class="flex items-center justify-between min-w-[20rem]">
      <div class="flex flex-col">
        <span class="font-semibold">{{opt.name}}</span>
        <span>{{opt.desc}}</span>
      </div>
      <div class="flex items-center gap-3">
        <button @click="opt.count--" :class="{'disabled-btn': opt.count === 0}" class="border-2 border-gray-400 rounded-full w-8 h-8 hover:bg-gray-200 flex items-center justify-center">-</button>
        {{opt.count}}
        <button @click="opt.count++" class="border-2 border-gray-400 rounded-full w-8 h-8 hover:bg-gray-200">+</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data(){
    return{
      options:[
        {
          id: 1,
          name: "Adults",
          desc: "Ages 13 or above",
          count: 0
        },
        {
          id: 2,
          name: "Children",
          desc: "Ages 2-12",
          count: 0
        },
        {
          id: 3,
          name: "Infants",
          desc: "Under 2",
          count: 0
        },
        {
          id: 4,
          name: "Pets",
          count: 0
        },
      ]
    }
  }
}
</script>

<style>
</style>