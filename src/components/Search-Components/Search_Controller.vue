<template>
  <div class="flex items-center justify-center sm:justify-evenly w-auto mb-4">
    <div class="items-center flex flex-col max-sm:gap-3 sm:flex-row w-full sm:w-auto h-screen sm:h-auto absolute top-0 bg-gray-100
               sm:bg-gray-200 sm:rounded-full shadow-lg cursor-pointer sm:relative max-sm:px-3 max-sm:pb-2" id="controller">

      <div class="py-4 w-full flex sm:hidden justify-center gap-8 text-lg font-semibold">
        <span class="underline">Stays</span>
        <span>Experiences</span>
      </div>
      <div class="absolute top-4 left-4 sm:hidden">
        <svg @click="emitCloseCont()" class="hover:bg-white rounded-full" xmlns="http://www.w3.org/2000/svg" width="40" height="40" enable-background="new 0 0 24 24" viewBox="0 0 24 24"><path d="M12.0119629,2.0039062C6.491272,2.0006104,2.0131836,6.4733276,2.0098877,11.9940186S6.4793091,21.9927979,12,21.9960938c2.6522827,0.0043335,5.1970215-1.0482178,7.0712891-2.9248047c1.875-1.8734131,2.9291992-4.4147949,2.9307861-7.0653076C22.0053711,6.4852905,17.5326538,2.0072021,12.0119629,2.0039062z M12.0122681,20.9960938c-4.9684448,0.0033569-8.9988403-4.0215454-9.0022583-8.9899902C3.0066528,7.0377197,7.0316162,3.0072632,12,3.0039062c2.387085-0.0042725,4.6774292,0.9428711,6.3642578,2.6318359c1.687439,1.6858521,2.6363525,3.9728394,2.6379395,6.3581543C21.0056152,16.9622803,16.9806519,20.9926758,12.0122681,20.9960938z M12.7069702,12l3.1816406-3.1816406c0.1905518-0.194397,0.1905518-0.5054932,0-0.6998901c-0.1932373-0.1972046-0.5097656-0.2003784-0.7069702-0.0071411L12,11.2929688L8.8183594,8.1113892c-0.194397-0.1904907-0.5054932-0.1904907-0.6998901,0C7.9212646,8.3046265,7.9180908,8.6211548,8.1113281,8.8183594L11.2929688,12l-3.1816406,3.1816406c-0.09375,0.09375-0.1463623,0.2208862-0.1464233,0.3534546c0,0.276123,0.2238159,0.5,0.499939,0.500061c0.1326294,0.0001831,0.2598877-0.0525513,0.3535156-0.1464844L12,12.7070312l3.1816406,3.1816406c0.0936279,0.0939331,0.2208862,0.1466675,0.3535156,0.1464844v0.000061c0.1325684-0.000061,0.2596436-0.0527344,0.3533936-0.1464233c0.1953125-0.1952515,0.1953125-0.5118408,0.000061-0.7071533L12.7069702,12z"/></svg>
      </div>

      <!--Location button-->
      <div class="relative max-sm:w-full">
        <button class="max-sm:bg-white flex flex-col w-full sm:hover:bg-gray-300 sm:pl-8 max-sm:px-6 sm:pr-28 sm:h-16 justify-center 
                      max-sm:rounded-2xl rounded-full max-sm:py-4 max-sm:shadow-md transition-all" id="1" 
              @click="selected_picker = 'location_picker'"
              :class="{'bg-white sm:hover:bg-white shadow-center': selected_picker == 'location_picker'}">

          <section class="hidden sm:flex flex-col items-start">
            <span class="font-semibold text-sm pointer-events-none">Where</span>
            <input type="text" placeholder="Search destinations" v-model="location_query"
                    class=" focus:outline-none focus:border-none bg-transparent">
            
          </section>

          <section class="flex sm:hidden w-full">
            <div v-if="selected_picker == 'location_picker'" class="flex flex-col items-start w-full">
              <span class="font-semibold text-2xl pointer-events-none mb-3" >Where to?</span>
              <div class="flex items-center w-full relative ">
                <svg class="absolute left-4 bottom-1/2" version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" width="16" height="16" viewBox="0 0 122.879 119.799" enable-background="new 0 0 122.879 119.799" xml:space="preserve"><g><path d="M49.988,0h0.016v0.007C63.803,0.011,76.298,5.608,85.34,14.652c9.027,9.031,14.619,21.515,14.628,35.303h0.007v0.033v0.04 h-0.007c-0.005,5.557-0.917,10.905-2.594,15.892c-0.281,0.837-0.575,1.641-0.877,2.409v0.007c-1.446,3.66-3.315,7.12-5.547,10.307 l29.082,26.139l0.018,0.016l0.157,0.146l0.011,0.011c1.642,1.563,2.536,3.656,2.649,5.78c0.11,2.1-0.543,4.248-1.979,5.971 l-0.011,0.016l-0.175,0.203l-0.035,0.035l-0.146,0.16l-0.016,0.021c-1.565,1.642-3.654,2.534-5.78,2.646 c-2.097,0.111-4.247-0.54-5.971-1.978l-0.015-0.011l-0.204-0.175l-0.029-0.024L78.761,90.865c-0.88,0.62-1.778,1.209-2.687,1.765 c-1.233,0.755-2.51,1.466-3.813,2.115c-6.699,3.342-14.269,5.222-22.272,5.222v0.007h-0.016v-0.007 c-13.799-0.004-26.296-5.601-35.338-14.645C5.605,76.291,0.016,63.805,0.007,50.021H0v-0.033v-0.016h0.007 c0.004-13.799,5.601-26.296,14.645-35.338C23.683,5.608,36.167,0.016,49.955,0.007V0H49.988L49.988,0z M50.004,11.21v0.007h-0.016 h-0.033V11.21c-10.686,0.007-20.372,4.35-27.384,11.359C15.56,29.578,11.213,39.274,11.21,49.973h0.007v0.016v0.033H11.21 c0.007,10.686,4.347,20.367,11.359,27.381c7.009,7.012,16.705,11.359,27.403,11.361v-0.007h0.016h0.033v0.007 c10.686-0.007,20.368-4.348,27.382-11.359c7.011-7.009,11.358-16.702,11.36-27.4h-0.006v-0.016v-0.033h0.006 c-0.006-10.686-4.35-20.372-11.358-27.384C70.396,15.56,60.703,11.213,50.004,11.21L50.004,11.21z"/></g></svg>
                <input type="text" placeholder="Search destinations" v-model="location_query"
                    class="w-full focus:outline-none border-[0.12rem] border-gray-400 rounded-lg py-4 pl-10 bg-transparent mb-4">
              </div>
              
            </div>
            
            <div class="flex items-center justify-between w-full" v-else>
              <span class="pointer-events-none">Where</span>
              <span class="font-semibold">{{location_query || "I'm flexible"}}</span>
            </div>
            
          </section>

          <div class="sm:p-8 sm:bg-white sm:rounded-3xl sm:shadow-lg sm:absolute sm:top-20 w-full sm:min-w-max sm:left-0  
                      max-sm:overflow-x-scroll" 
              v-show="selected_picker == 'location_picker'">
              <keep-alive>
                <location_picker :search_query="location_query" :clear_signal="clearSignal" @regionSelect="getSelectedRegion"
                                @locationSelect="getSelectedLocation"/>
              </keep-alive>
            </div>

            <div class="absolute right-5 bg-gray-200 p-1 rounded-full hover:bg-gray-300 transition-all hidden sm:block"
              v-show="selected_picker == 'location_picker' && (location_query !== '' || selected_region)"
              @click="clearData()">
              <svg xmlns="http://www.w3.org/2000/svg" width="17" height="17" viewBox="0 0 24 24"><path fill="none" d="M0 0h24v24H0V0z"/><path d="M18.3 5.71c-.39-.39-1.02-.39-1.41 0L12 10.59 7.11 5.7c-.39-.39-1.02-.39-1.41 0-.39.39-.39 1.02 0 1.41L10.59 12 5.7 16.89c-.39.39-.39 1.02 0 1.41.39.39 1.02.39 1.41 0L12 13.41l4.89 4.89c.39.39 1.02.39 1.41 0 .39-.39.39-1.02 0-1.41L13.41 12l4.89-4.89c.38-.38.38-1.02 0-1.4z"/></svg>
            </div>
        </button>
      </div>

      <p class="max-sm:hidden w-[0.12rem] h-6 bg-gray-300"></p>

      <!--Date button-->
      <div class="flex max-sm:flex-col items-center justify-center transition-all w-full sm:w-64" id="2"
          :class="{'max-sm:h-full': selected_picker == 'date_picker'}">
        <section class="hidden sm:block w-full">
          <button v-if="selected_flex_type == 2" class="flex flex-col justify-center px-6 h-16 w-full rounded-full hover:bg-gray-300"
                @click="selected_picker = 'date_picker'"
                :class="{'bg-white sm:hover:bg-white shadow-center': selected_picker == 'date_picker' || selected_picker == 'date_picker_out'}">
            <span class="font-semibold text-sm pointer-events-none">When</span>
            <div class="flex items-center">
              <span class="font-light pointer-events-none">
                <span v-if="!selected_months || monthsLength === 0">Any</span>
                {{selected_flex_opt}}
                <span v-if="selected_months && monthsLength > 0">in</span>
              </span>
              <div class="flex items-center ml-1 w-20" v-if="selected_months && monthsLength > 0">
                <span class="min-w-max" v-for="mon of selected_months.slice(0, 3)" :key="mon">
                  {{mon.substring(0, 3)}}
                  <span class="mr-1 -ml-1" v-if="monthsLength > 1">,</span>
                </span>
                <span v-if="monthsLength > 3">...</span>
              </div>
            </div>
          </button>

          <div v-else class="flex items-center justify-center w-full">
            <button class="flex flex-col justify-center rounded-full hover:bg-gray-300 h-16 px-6 w-32"
              @click="selected_picker = 'date_picker'"
              :class="{'bg-white sm:hover:bg-white shadow-center': selected_picker == 'date_picker'}">
              <span class="font-semibold text-sm pointer-events-none">Check in</span>
              <span class="font-light pointer-events-none">
                {{selected_date ? selected_date.c_in_month + " " +  selected_date.c_in_day : 'Add dates'}}
              </span>
            </button>

            <p class="sm:w-[0.12rem] h-6 bg-gray-300"></p>

            <button class="flex flex-col justify-center rounded-full hover:bg-gray-300 h-16 px-6 w-32"
              @click="selected_picker = 'date_picker_out'"
              :class="{'bg-white sm:hover:bg-white shadow-center': selected_picker == 'date_picker_out'}">
              <span class="font-semibold text-sm pointer-events-none">Check out</span>
              <span class=" font-light pointer-events-none">
                {{selected_date ? selected_date.c_out_month + " " +  selected_date.c_out_day : 'Add dates'}}
              </span>
            </button>
          </div>
        </section>

        <section class="sm:hidden w-full" @click="selected_picker = 'date_picker'">
          <button v-if="selected_picker != 'date_picker' " class="flex item-center justify-between w-full rounded-2xl bg-white px-6 py-4 shadow-md">
            <span>When</span>
            <span class="font-semibold">Add dates</span>
          </button>
        </section>

        <div class="sm:p-8 bg-white rounded-t-2xl sm:rounded-3xl min-h-full sm:shadow-lg sm:absolute sm:top-20 w-full sm:left-0 
                    max-sm:flex max-sm:flex-col overflow-x-hiddenm max-sm:justify-between"
          v-show="selected_picker == 'date_picker' || selected_picker == 'date_picker_out'">
          <span class="sm:hidden font-semibold text-2xl pointer-events-none ml-6 mt-4 mb-5" >When's your trip?</span>
          <keep-alive>
            <date_picker  @dateInput="getSelectedDate" 
                          @emitDateInput="getSelectedDate"
                          @selected_months="getSelectedMonths"
                          @flexible="getFlexibleType"
                          @flexible_opt="getFlexibleOpt"/>  
          </keep-alive>
          <div class="flex sm:hidden items center w-full justify-between px-6 border-y-[0.12rem] py-3 border-gray-300">
            <button class="font-semibold text-lg underline hover:bg-gray-100 rounded-lg transition-all px-4"
                    @click="selected_picker = 'guests_picker'">Skip</button>
            <button class="text-white bg-gray-800 rounded-lg px-4 py-2 font-semibold text-lg hover:bg-black transition-all"
                    @click="selected_picker = 'guests_picker'">Next</button>
          </div>  
         
        </div>
      </div>

      <p class="max-sm:hidden w-[0.12rem] h-6 bg-gray-300"></p>

      <!--Guests button-->
      <div class="relative max-sm:w-full" :class="{'max-sm:hidden': selected_picker == 'date_picker'}">
        <button class="hidden sm:flex items-center justify-between w-[15rem] max-sm:bg-white sm:hover:bg-gray-300 h-16 px-2 pl-6 rounded-full
                        transition-all" id="4" 
              @click="selected_picker = 'guests_picker'"
              :class="{'bg-white sm:hover:bg-white shadow-center': selected_picker == 'guests_picker'}">

          <div class="flex flex-col items-start pointer-events-none">
            <span class="font-semibold text-sm pointer-events-none">Who</span>
            <span class=" font-light">Add guests</span>
          </div>
          <div class="px-4 py-3 sm:bg-rose-500 rounded-full flex items-center gap-3 absolute right-2"
              @click="emitSearch()">
            <svg class="sm:fill-white" version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" width="16" height="16" viewBox="0 0 122.879 119.799" enable-background="new 0 0 122.879 119.799" xml:space="preserve"><g><path d="M49.988,0h0.016v0.007C63.803,0.011,76.298,5.608,85.34,14.652c9.027,9.031,14.619,21.515,14.628,35.303h0.007v0.033v0.04 h-0.007c-0.005,5.557-0.917,10.905-2.594,15.892c-0.281,0.837-0.575,1.641-0.877,2.409v0.007c-1.446,3.66-3.315,7.12-5.547,10.307 l29.082,26.139l0.018,0.016l0.157,0.146l0.011,0.011c1.642,1.563,2.536,3.656,2.649,5.78c0.11,2.1-0.543,4.248-1.979,5.971 l-0.011,0.016l-0.175,0.203l-0.035,0.035l-0.146,0.16l-0.016,0.021c-1.565,1.642-3.654,2.534-5.78,2.646 c-2.097,0.111-4.247-0.54-5.971-1.978l-0.015-0.011l-0.204-0.175l-0.029-0.024L78.761,90.865c-0.88,0.62-1.778,1.209-2.687,1.765 c-1.233,0.755-2.51,1.466-3.813,2.115c-6.699,3.342-14.269,5.222-22.272,5.222v0.007h-0.016v-0.007 c-13.799-0.004-26.296-5.601-35.338-14.645C5.605,76.291,0.016,63.805,0.007,50.021H0v-0.033v-0.016h0.007 c0.004-13.799,5.601-26.296,14.645-35.338C23.683,5.608,36.167,0.016,49.955,0.007V0H49.988L49.988,0z M50.004,11.21v0.007h-0.016 h-0.033V11.21c-10.686,0.007-20.372,4.35-27.384,11.359C15.56,29.578,11.213,39.274,11.21,49.973h0.007v0.016v0.033H11.21 c0.007,10.686,4.347,20.367,11.359,27.381c7.009,7.012,16.705,11.359,27.403,11.361v-0.007h0.016h0.033v0.007 c10.686-0.007,20.368-4.348,27.382-11.359c7.011-7.009,11.358-16.702,11.36-27.4h-0.006v-0.016v-0.033h0.006 c-0.006-10.686-4.35-20.372-11.358-27.384C70.396,15.56,60.703,11.213,50.004,11.21L50.004,11.21z"/></g></svg>
            <span class="text-white font-semibold">Search</span>
          </div>
        </button>

        <section class="sm:hidden w-full py-4 px-6 rounded-2xl flex items-center justify-between bg-white shadow-md"
          @click="selected_picker = 'guests_picker'"
          v-show="selected_picker != 'guests_picker'">
          <span>Who</span>
          <span class="font-semibold">Add guests</span>
        </section>

        <div class="p-5 sm:p-8 bg-white rounded-3xl shadow-lg sm:absolute top-72 sm:top-20 w-full sm:w-auto right-0" 
          v-show="selected_picker == 'guests_picker'">
          <keep-alive>
            <guests_picker @selectedGuests="getSelectedGuests"/>        
          </keep-alive>
        </div>
      </div>

      <div class="w-full absolute bottom-0 flex items-center justify-between px-6 py-2.5 bg-white sm:hidden"
        v-show="selected_picker != 'date_picker'">
        <button class="font-semibold underline hover:bg-gray-100 rounded-lg transition-all py-2 px-4" 
                @click="clearData()">Clear all</button>
        <div class="px-6 py-3 bg-rose-500 rounded-lg sm:rounded-full flex items-center gap-3"
            @click="emitSearch()">
          <svg class="fill-white" version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" width="16" height="16" viewBox="0 0 122.879 119.799" enable-background="new 0 0 122.879 119.799" xml:space="preserve"><g><path d="M49.988,0h0.016v0.007C63.803,0.011,76.298,5.608,85.34,14.652c9.027,9.031,14.619,21.515,14.628,35.303h0.007v0.033v0.04 h-0.007c-0.005,5.557-0.917,10.905-2.594,15.892c-0.281,0.837-0.575,1.641-0.877,2.409v0.007c-1.446,3.66-3.315,7.12-5.547,10.307 l29.082,26.139l0.018,0.016l0.157,0.146l0.011,0.011c1.642,1.563,2.536,3.656,2.649,5.78c0.11,2.1-0.543,4.248-1.979,5.971 l-0.011,0.016l-0.175,0.203l-0.035,0.035l-0.146,0.16l-0.016,0.021c-1.565,1.642-3.654,2.534-5.78,2.646 c-2.097,0.111-4.247-0.54-5.971-1.978l-0.015-0.011l-0.204-0.175l-0.029-0.024L78.761,90.865c-0.88,0.62-1.778,1.209-2.687,1.765 c-1.233,0.755-2.51,1.466-3.813,2.115c-6.699,3.342-14.269,5.222-22.272,5.222v0.007h-0.016v-0.007 c-13.799-0.004-26.296-5.601-35.338-14.645C5.605,76.291,0.016,63.805,0.007,50.021H0v-0.033v-0.016h0.007 c0.004-13.799,5.601-26.296,14.645-35.338C23.683,5.608,36.167,0.016,49.955,0.007V0H49.988L49.988,0z M50.004,11.21v0.007h-0.016 h-0.033V11.21c-10.686,0.007-20.372,4.35-27.384,11.359C15.56,29.578,11.213,39.274,11.21,49.973h0.007v0.016v0.033H11.21 c0.007,10.686,4.347,20.367,11.359,27.381c7.009,7.012,16.705,11.359,27.403,11.361v-0.007h0.016h0.033v0.007 c10.686-0.007,20.368-4.348,27.382-11.359c7.011-7.009,11.358-16.702,11.36-27.4h-0.006v-0.016v-0.033h0.006 c-0.006-10.686-4.35-20.372-11.358-27.384C70.396,15.56,60.703,11.213,50.004,11.21L50.004,11.21z"/></g></svg>
          <span class="text-white font-semibold">Search</span>
        </div>
      </div>
    </div>
  </div> 
</template>

<script>
import {date_picker, location_picker, guests_picker} from './Pickers'

export default {
  props:['picker_name'],
  components:{
    guests_picker, location_picker, date_picker
  },
  computed:{
    monthsLength(){
      if(this.selected_months){
        return this.selected_months.length
      }
      else{
        return 0
      }
    },
  },
  mounted(){
    this.selected_picker = this.picker_name
  },
  data(){
    return{
      selected_picker: 'location_picker',
      location_query: '',

      selected_date: null,
      selected_months: null,
      selected_flex_type: null,
      selected_flex_opt: null,
      selected_guests: null,
      selected_region: null,
      selected_location: null,

      clearSignal: false
    }
  },
  methods:{
    getSelectedDate(date){
      this.selected_date = date
    },
    getSelectedMonths(months){
      this.selected_months = months
      console.log(this.selected_months);
    },
    getFlexibleType(type){
      this.selected_flex_type = type
    },
    getFlexibleOpt(opt){
      this.selected_flex_opt = opt
    },
    getSelectedRegion(region){
      console.log(region);
      this.location_query = region
      this.selected_region = region
      this.selected_picker = "date_picker"
      console.log(this.selected_picker);
    },
    getSelectedLocation(data){
      this.selected_location = data
      this.location_query = data
      this.selected_picker = 'date_picker'
    },
    getSelectedGuests(data){
      this.selected_guests = data
      console.log('Guests:', this.selected_guests);
    },

    emitSearch(){
      this.$emit('search')
    },
    emitCloseCont(){
      this.$emit('closeCont')
    },

    clearData(){
      this.clearSignal = !this.clearSignal
      this.location_query = ''
      this.selected_region = null
    }
  }
}
</script>

<style>
</style>