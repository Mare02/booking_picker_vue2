<template>
  <div class="w-full flex flex-col fixed top-0 z-10">
    <div class="hidden sm:flex py-4 px-12 md:px-24  bg-gray-200 border-b-[0.1rem] border-gray-400 
                items-center justify-between">
      <div>
        <span class="text-[1.1rem] md:text-xl font-semibold">Introducing our 2022 Winter Release</span>
      </div>
      <div>
        <a href="">Explore what's new</a>
      </div>
    </div>
    <div class="px-2 py-3 sm:py-0 sm:pb-0 lg:px-24 shadow-lg sm:shadow-md bg-white border-gray-400 flex items-center sm:justify-between justify-center">

      <div class="items-center hidden sm:flex">
        <div class="w-20 h-20">
          <img class="w-full h-full" src="../assets/home_logo.png" alt="">
        </div>
        <span class="font-semibold text-lg hidden md:block">ExampleName</span>
      </div>

      <Search/>

      <div class="items-center gap-2 hidden sm:flex">
        <a href="">Language</a>
        <div class="border-[0.1rem] border-gray-400 rounded-2xl p-2">
          <a href="" class="font-semibold">Profile</a>
        </div>
      </div>

    </div>
  </div>
</template>

<script>
import Search from './Search-Components/Search_Toggler.vue' 
export default{
  components:{
    Search
  },
  computed:{

  },
  mounted(){

  },
  data(){
    return{

    }
  },
  methods:{

  }
}
</script>

<style>
</style>