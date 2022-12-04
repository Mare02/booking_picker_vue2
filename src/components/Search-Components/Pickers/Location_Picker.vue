<template>
  <div>
    <div class="flex flex-col" v-if="queryLength > 0">
      <div v-for="loc in locations_arr" :key="locations_arr.indexOf(loc)" class="flex items-center gap-4 hover:bg-gray-200/50 px-4 
                                                                                  py-2 cursor-pointer min-w-[20rem]"
                                                                            @click="selectLoc(loc.address.formattedAddress)">
        <div class="p-3 bg-gray-200 rounded-xl">
          <svg class="w-6 h-6" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 32 32"><g data-name="Layer 2"><path d="M16,30a1,1,0,0,0,.62-.22C17,29.44,27,21.38,27,13A11,11,0,0,0,5,13c0,8.38,10,16.44,10.38,16.78A1,1,0,0,0,16,30ZM7,13a9,9,0,0,1,18,0c0,6.3-6.87,12.81-9,14.69C13.87,25.81,7,19.3,7,13Z"/><path d="M21,13a5,5,0,1,0-5,5A5,5,0,0,0,21,13Zm-8,0a3,3,0,1,1,3,3A3,3,0,0,1,13,13Z"/></g></svg>
        </div>
        <span class="text-lg">{{loc.address.formattedAddress}}</span>
      </div>
    </div>

    <div class="flex flex-col w-full mb-4" v-if="locationsLength === 0 || queryLength === 0">
      <span class="font-bold text-md mb-6 max-sm:hidden">Search by region</span>
      <div class="flex sm:flex-wrap gap-4 sm:justify-center items-start w-[28rem]">
        <div v-for="mapOpt in regionsArr" :key="mapOpt.id" class="flex flex-col items-start">
          <img class=" min-w-[8rem] min-h-[8rem] sm:w-32 sm:h-32 object-cover border-[0.13rem] border-gray-300 rounded-2xl hover:border-gray-400 cursor-pointer" 
                :src="mapOpt.img_url" alt=""
                :class="{'border-[0.2rem] border-gray-500': selected_region === mapOpt.name}"
                @click="selectRegion(mapOpt.name)">
          <span class="mb-2">{{mapOpt.name}}</span>
        </div>
      </div>
    </div>
    
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name:'location-picker',
  props:['search_query', 'clear_signal'],
  mounted(){
    
  },
  computed:{
    queryLength(){
      return this.search_query.length
    },
    locationsLength(){
      return this.locations_arr.length
    }
  },
  watch:{
    search_query(){
      this.getLocations()
    },
    selected_region(){
      if (this.selected_region && this.selected_region !== ''){
        this.locations_arr = []
      }
    },
    selected_location(){
      this.$emit('locationSelect', this.selected_location)
    },
    clear_signal(){
      this.selected_region = null
      this.locations_arr = []
      this.selected_location = ''
      console.log('clear signal');
    }
  },
  data(){
    return{
      bing_maps_key: 'AgHPai2_f_uHB1ftS5vQLzvSRcP7qgGW-lxFGSof_AULvD3eRtywQLjFgB-DYU8F',

      locations_arr: [],
      selected_region: null,
      selected_location: '',

      regionsArr:[
        {
          id: 0,
          name: "I'm flexible",
          img_url: 'https://img.freepik.com/free-vector/grey-world-map_1053-431.jpg'
        },
        {
          id: 1,
          name: 'Europe',
          img_url: 'https://vemaps.com/uploads/img/big/eu-c-03.jpg'
        },
        {
          id: 2,
          name: 'France',
          img_url: 'https://www.shutterstock.com/image-vector/black-flat-map-kingdom-italy-260nw-1745409068.jpg'
        },
        {
          id: 3,
          name: 'United States',
          img_url: 'https://cdn.europosters.eu/image/750/art-photo/map-of-north-america-in-grayscale-i95883.jpg'
        },
        {
          id: 4,
          name: 'United Kingdom',
          img_url: 'https://img.myloview.cz/nalepky/the-great-britain-map-in-gray-on-a-white-background-400-113821663.jpg'
        },
        {
          id: 5,
          name: 'South America',
          img_url: 'https://thumbs.dreamstime.com/b/map-south-america-gray-color-white-background-83884976.jpg'
        },
      ]
    }
  },
  methods:{
    async getLocations(){
      if(this.search_query !== ''){
        try {
          let res = await axios.get(`http://dev.virtualearth.net/REST/v1/Locations?query=${this.search_query}&key=${this.bing_maps_key}`)
          console.log(res.data.resourceSets[0].resources);
          this.locations_arr = res.data.resourceSets[0].resources
        } 
        catch (error) {
          console.log(error); 
        }
      }
    },
    selectRegion(region){
      this.selected_region = region
      this.$emit('regionSelect', region)
    },
    selectLoc(location){
      this.selected_location = location
    }
  }
}
</script>

<style>
</style>