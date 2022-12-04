<template>
  <div class="flex flex-col gap-5">
    <span class="sm:hidden font-semibold text-2xl">Who's coming?</span>
    <div v-for="opt in options" :key="opt.id" class="flex items-center justify-between min-w-[20rem] flex-wrap">
      <div class="flex flex-col">
        <span class="font-semibold">{{opt.name}}</span>
        <span>{{opt.desc}}</span>
      </div>
      <div class="flex items-center gap-3">
        <button :class="{'pointer-events-none': opt.count === 0}" @click="opt.count--">
          <svg class="opacity-50 hover:opacity-90" :class="{'opacity-10': opt.count === 0}" xmlns="http://www.w3.org/2000/svg" width="37" height="37" id="Layer_1" x="0" y="0" version="1.1" viewBox="0 0 29 29" xml:space="preserve"><path d="M14.5 27.071c-6.893 0-12.5-5.607-12.5-12.5s5.607-12.5 12.5-12.5S27 7.678 27 14.571s-5.607 12.5-12.5 12.5zm0-23c-5.79 0-10.5 4.71-10.5 10.5s4.71 10.5 10.5 10.5S25 20.36 25 14.571s-4.71-10.5-10.5-10.5z"/><path d="M20.5 15.571h-12a1 1 0 0 1 0-2h12a1 1 0 0 1 0 2z"/></svg>
        </button>
        {{opt.count}}
        <button :class="{'pointer-events-none': opt.count >= 5}" @click="opt.count++">
          <svg class="p-[2px] opacity-50 hover:opacity-90" :class="{'opacity-10': opt.count >= 5}" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1" width="37" height="37" viewBox="0 0 256 256" xml:space="preserve"><defs></defs><g style="stroke: none; stroke-width: 0; stroke-dasharray: none; stroke-linecap: butt; stroke-linejoin: miter; stroke-miterlimit: 10; fill: none; fill-rule: nonzero; opacity: 1;" transform="translate(1.4065934065934016 1.4065934065934016) scale(2.81 2.81)" ><path d="M 45 69.478 c -1.657 0 -3 -1.343 -3 -3 V 23.523 c 0 -1.657 1.343 -3 3 -3 c 1.657 0 3 1.343 3 3 v 42.955 C 48 68.135 46.657 69.478 45 69.478 z" style="stroke: none; stroke-width: 1; stroke-dasharray: none; stroke-linecap: butt; stroke-linejoin: miter; stroke-miterlimit: 10; fill: rgb(0,0,0); fill-rule: nonzero; opacity: 1;" transform=" matrix(1 0 0 1 0 0) " stroke-linecap="round" /><path d="M 66.478 48 H 23.523 c -1.657 0 -3 -1.343 -3 -3 c 0 -1.657 1.343 -3 3 -3 h 42.955 c 1.657 0 3 1.343 3 3 C 69.478 46.657 68.135 48 66.478 48 z" style="stroke: none; stroke-width: 1; stroke-dasharray: none; stroke-linecap: butt; stroke-linejoin: miter; stroke-miterlimit: 10; fill: rgb(0,0,0); fill-rule: nonzero; opacity: 1;" transform=" matrix(1 0 0 1 0 0) " stroke-linecap="round" /><path d="M 45 90 C 20.187 90 0 69.813 0 45 C 0 20.187 20.187 0 45 0 c 24.813 0 45 20.187 45 45 C 90 69.813 69.813 90 45 90 z M 45 6 C 23.495 6 6 23.495 6 45 s 17.495 39 39 39 s 39 -17.495 39 -39 S 66.505 6 45 6 z" style="stroke: none; stroke-width: 1; stroke-dasharray: none; stroke-linecap: butt; stroke-linejoin: miter; stroke-miterlimit: 10; fill: rgb(0,0,0); fill-rule: nonzero; opacity: 1;" transform=" matrix(1 0 0 1 0 0) " stroke-linecap="round" /></g></svg>
        </button>
      </div>
      <p class="w-full h-[0.1rem] mt-5 bg-gray-200" v-if="opt.id < 4"></p>
    </div>
    
  </div>
</template>

<script>
export default {
  name:'guests-picker',
  computed:{
    
  },
  watch:{
    
  },
  updated(){
    console.log('updated');

    console.log('----------------------------');
    for(let opt of this.options){
      console.log(opt.name + ":", opt.count);
      let obj = {
        name: opt.name,
        count: opt.count
      }
      this.selectedOptArr.push(obj)
    }
  },
  data(){
    return{
      selectedOptArr: [],
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
          desc: "Bringing a service animal?",
          count: 0
        },
      ]
    }
  },
  methods:{

  }
}
</script>

<style>
</style>