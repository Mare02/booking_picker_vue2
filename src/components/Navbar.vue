<template>
  <div class="w-full flex flex-col fixed top-0 z-10" :class="{'dim-sibling': false}">
    <div class="hidden sm:flex px-12 py-4 md:px-24 bg-gray-200 border-b-[0.1rem] border-gray-400 
                items-center justify-between">
      <div>
        <span class="text-[1.1rem] md:text-xl font-semibold">Introducing our 2022 Winter Release</span>
      </div>
      <div>
        <a href="">Explore what's new</a>
      </div>
    </div>
    <div class="flex flex-col bg-white shadow-lg sm:shadow-md">
      <div class="max-sm:px-4 py-3 sm:py-0 sm:pb-0 lg:px-24 flex items-center sm:justify-between justify-center">
        <div class="items-center hidden sm:flex">
          <div class="w-20 h-20 flex items-center justify-center  mr-[-0.5rem]">
            <img class="md:w-full md:h-full w-4/5 h-4/5" src="../assets/home_logo.png" alt="">
          </div>
          <span class="font-semibold text-lg hidden md:block">Brand Name</span>
        </div>
        <transition :name="toggler_animation">
          <Search_Toggler v-if="!showMainComponent" @emitShowMain="showMain"/>
        </transition>
        <div class="items-center gap-2 hidden sm:flex">
          <a href="">Language</a>
          <div class="border-[0.1rem] border-gray-400 rounded-2xl p-2">
            <a href="" class="font-semibold">Profile</a>
          </div>
        </div>
      </div>
      <transition :name="cont_animation">
        <Search_Controller v-if="showMainComponent" :picker_name="selectedPickerName" @search="showMainComponent = false"
                            @closeCont="showMainComponent = false"/>
      </transition>
    </div>
    <div class="w-full top-0 absolute h-screen bg-black/40 z-[-1]" v-if="showMainComponent" id="dim"></div>
  </div>
</template>

<script>
import Search_Toggler from './Search-Components/Search_Toggler.vue' 
import Search_Controller from '../components/Search-Components/Search_Controller.vue';

const x = window.matchMedia("(max-width: 680px)")

export default{
  components:{
    Search_Toggler, Search_Controller
  },
  computed:{

  },
  mounted(){
    if(x.matches){
      this.cont_animation = 'fade_mobile'
      this.toggler_animation = 'fade_mobile_rev'
    }
    window.addEventListener('resize', () => {
      if(x.matches){
        this.showMainComponent = false
        this.cont_animation = 'fade_mobile'
        this.toggler_animation = 'fade_mobile_rev'
      }
      else{
        this.cont_animation = 'fade'
        this.toggler_animation = 'fade_rev'
      }
    })
    document.addEventListener('click', (e) => {
      if(e.target.id === 'dim'){
        this.showMainComponent = false
      }
    })
  },
  data(){
    return{
      showMainComponent: false,
      selectedPickerName: null,
      cont_animation: 'fade',
      toggler_animation: 'fade_rev'
    }
  },
  methods:{
    showMain(param){
      this.selectedPickerName = param
      this.showMainComponent = !this.showMainComponent
    },
  }
}
</script>

<style>
.fade-enter-active, .fade-leave-active {
  transition: all .2s ease;
  max-height: 1200px;
  overflow: hidden;
}
.fade-enter, .fade-leave-to{
  transform: translateY(-3rem);
  opacity: 0;
  transition: all .2s ease;
  scale: 0.8;
  max-height: 0;
}

.fade_rev-enter-active, .fade_rev-leave-active {
  transition: all .2s ease;
  opacity: 1;
  max-height: 1200px;
  overflow: hidden;
}
.fade_rev-enter, .fade_rev-leave-to{
  opacity: 0;
  transition: all .2s ease;
  transform: translateY(3rem);
  scale: 1.5;
  max-height: 0;
}

.fade_mobile-enter-active, .fade_mobile-leave-active {
  transition: all .4s ease;
  transform: translateY(0rem);
}
.fade_mobile-enter, .fade_mobile-leave-to{
  transition: all .5s;
  transform: translateY(200rem);
}

.fade_mobile_rev-enter-active, .fade_mobile_rev-leave-active {

}
.fade_mobile_rev-enter, .fade_mobile_rev-leave-to{

}

</style>