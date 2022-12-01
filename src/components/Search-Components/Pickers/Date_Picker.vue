<template>
  <div class="flex flex-col items-center">
    <div class="flex items-center gap-1 p-1 bg-gray-300 rounded-full w-1/2 font-semibold mb-4">
      <span :class="{'bg-white': selected_type == 1}" class="rounded-full text-center transition-all px-4 py-2 cursor-pointer w-1/2" @click="selectType" id="1">Choose dates</span>
      <span :class="{'bg-white': selected_type == 2}" class="rounded-full text-center transition-all px-4 py-2 cursor-pointer w-1/2" @click="selectType" id="2">I'm flexible</span>
    </div>
    <date-range-picker v-model="date_range" :autoApply="true" :opens="'inline'" :ranges="false" @update="emitDateInput()"/>
  </div>
</template>

<script>
import DateRangePicker from 'vue2-daterange-picker'
import 'vue2-daterange-picker/dist/vue2-daterange-picker.css'

export default {
  name:'date-picker',
  components:{
    DateRangePicker
  },
  computed:{
    selected_date(){
      let check_in_month = new Date(this.date_range.startDate).toLocaleString('default', { month: 'long' }).substring(0, 3);
      let check_in_day = new Date(this.date_range.startDate).getDate()
      let check_out_month = new Date(this.date_range.endDate).toLocaleString('default', { month: 'long' }).substring(0, 3);
      let check_out_day = new Date(this.date_range.endDate).getDate()

      return {"c_in_month": check_in_month, 
              "c_in_day": check_in_day, 
              "c_out_month": check_out_month, 
              "c_out_day": check_out_day};
    }
  },
  data(){
    return{
      check_in: null,
      check_out: null,
      date_range: {},

      selected_type: 1
    }
  },
  methods:{
    emitDateInput(){
      console.log('emit');
      console.log(Date(this.date_range.startDate).toLocaleString('default', { month: 'long' }).substring(0, 3));
      this.$emit('dateInput', this.selected_date)
    },
    selectType(e){
      this.selected_type = e.target.id
    }
  }
}
</script>

<style>
</style>