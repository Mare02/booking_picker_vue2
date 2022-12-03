<template>
  <div class="flex flex-col items-center max-h-fit max-sm:w-full">
    <div class="flex items-center gap-1 p-1 bg-gray-300 rounded-full w-80 font-medium mb-4">
      <span :class="{'bg-white': selected_type == 1}" class="rounded-full text-center transition-all px-6 py-[0.3rem] cursor-pointer w-1/2 hover:bg-gray-200/90" @click="selectType" id="1">Choose dates</span>
      <span :class="{'bg-white': selected_type == 2}" class="rounded-full text-center transition-all px-6 py-[0.3rem] cursor-pointer w-1/2 hover:bg-gray-200/90" @click="selectType" id="2">I'm flexible</span>
    </div>
    <date-range-picker v-if="selected_type == 1" v-model="date_range" 
                      :autoApply="true" 
                      :opens="'inline'" 
                      :ranges="false" 
                      @update="emitDateInput()"/>
    <div class="flex flex-col items-center max-sm:w-full" v-if="selected_type == 2">
      <span class="font-semibold text-xl mb-4 mt-2">Stay for a {{selected_flexible_opt}}</span>
      <div class="flex items-center gap-2">
        <div v-for="opt in flexible_options" :key="opt.id" class="px-3 py-1 border-[0.12rem] border-gray-300 hover:border-gray-400 rounded-full cursor-pointer"
              @click="selected_flexible_opt = opt.name" :class="{'border-[0.2rem] border-gray-500': selected_flexible_opt === opt.name}">
          {{opt.name}}
        </div>
      </div>

      <span class="font-semibold text-xl mb-4 mt-9">Go anytime</span>
      <div class="flex items-center gap-4 pb-8 w-full sm:max-w-2xl max-sm:px-4 overflow-x-scroll">
        <div v-for="mon in months" :key="mon.monthId" class="flex flex-col justify-center items-center min-w-[8rem] min-h-[10rem] 
                                                            rounded-lg border-[0.15rem] cursor-pointer"
              :class="{'border-gray-400': selected_months.includes(mon.monthName)}"
              @click="selectMonth(mon.monthName)">
          <svg class="w-8 h-8" id="Layer_1" data-name="Layer 1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 122.88 122.89"><title>date</title><path d="M81.61,4.73C81.61,2.12,84.19,0,87.38,0s5.77,2.12,5.77,4.73V25.45c0,2.61-2.58,4.73-5.77,4.73s-5.77-2.12-5.77-4.73V4.73ZM66.11,105.66c-.8,0-.8-10.1,0-10.1H81.9c.8,0,.8,10.1,0,10.1ZM15.85,68.94c-.8,0-.8-10.1,0-10.1H31.64c.8,0,.8,10.1,0,10.1Zm25.13,0c-.8,0-.8-10.1,0-10.1H56.77c.8,0,.8,10.1,0,10.1Zm25.13,0c-.8,0-.8-10.1,0-10.1H81.9c.8,0,.8,10.1,0,10.1Zm25.14-10.1H107c.8,0,.8,10.1,0,10.1H91.25c-.8,0-.8-10.1,0-10.1ZM15.85,87.3c-.8,0-.8-10.1,0-10.1H31.64c.8,0,.8,10.1,0,10.1ZM41,87.3c-.8,0-.8-10.1,0-10.1H56.77c.8,0,.8,10.1,0,10.1Zm25.13,0c-.8,0-.8-10.1,0-10.1H81.9c.8,0,.8,10.1,0,10.1Zm25.14,0c-.8,0-.8-10.1,0-10.1H107c.8,0,.8,10.1,0,10.1Zm-75.4,18.36c-.8,0-.8-10.1,0-10.1H31.64c.8,0,.8,10.1,0,10.1Zm25.13,0c-.8,0-.8-10.1,0-10.1H56.77c.8,0,.8,10.1,0,10.1ZM29.61,4.73C29.61,2.12,32.19,0,35.38,0s5.77,2.12,5.77,4.73V25.45c0,2.61-2.58,4.73-5.77,4.73s-5.77-2.12-5.77-4.73V4.73ZM6.4,43.47H116.47v-22a3,3,0,0,0-.86-2.07,2.92,2.92,0,0,0-2.07-.86H103a3.2,3.2,0,0,1,0-6.4h10.55a9.36,9.36,0,0,1,9.33,9.33v92.09a9.36,9.36,0,0,1-9.33,9.33H9.33A9.36,9.36,0,0,1,0,113.55V21.47a9.36,9.36,0,0,1,9.33-9.33H20.6a3.2,3.2,0,1,1,0,6.4H9.33a3,3,0,0,0-2.07.86,2.92,2.92,0,0,0-.86,2.07v22Zm110.08,6.41H6.4v63.67a3,3,0,0,0,.86,2.07,2.92,2.92,0,0,0,2.07.86H113.55a3,3,0,0,0,2.07-.86,2.92,2.92,0,0,0,.86-2.07V49.88ZM50.43,18.54a3.2,3.2,0,0,1,0-6.4H71.92a3.2,3.2,0,1,1,0,6.4Z"/></svg>
          {{mon.monthName}}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import DateRangePicker from 'vue2-daterange-picker'
import 'vue2-daterange-picker/dist/vue2-daterange-picker.css'
import moment from 'moment'

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
  mounted(){
    this.getMonths()
  },
  data(){
    return{
      check_in: null,
      check_out: null,
      date_range: {},

      selected_type: 1,
      selected_months: [],
      selected_flexible_opt: 'Week',

      flexible_options:[
        {
          id: 1,
          name: 'Weekend'
        },
        {
          id: 2,
          name: 'Week'
        },
        {
          id: 3,
          name: 'Month'
        }
      ],
      months: []
    }
  },
  watch:{
    selected_type(){
      this.$emit('flexible', this.selected_type)
      this.$emit('flexible_opt', this.selected_flexible_opt)
    },
    selected_flexible_opt(){
      this.$emit('flexible_opt', this.selected_flexible_opt)
    }
  },
  methods:{
    emitDateInput(){
      this.$emit('dateInput', this.selected_date)
    },
    selectType(e){
      this.selected_type = e.target.id
    },
    getMonths(){
      let months = []
      let dateStart = moment()
      let dateEnd = moment().add(10, 'month')
      while (dateEnd.diff(dateStart, 'months') >= 0) {
        const obj = {
          monthId: dateStart.format('M'),
          monthName: this.getMonthName(dateStart.format('M'))
        }
        months.push(obj)
        dateStart.add(1, 'month')
      }
      this.months = months
    },
    getMonthName(monthNumber){
      let date = new Date();
      date.setMonth(monthNumber-1);
      return date.toLocaleString('en-US', { month: 'long' });
    },
    selectMonth(month){
      if(!this.selected_months.includes(month)){
        this.selected_months.push(month)
      }
      else{
        let index = this.selected_months.indexOf(month)
        this.selected_months.splice(index, 1)
      }
      this.$emit('selected_months', this.selected_months)
    }
  }
}
</script>

<style>
</style>