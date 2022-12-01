<template>
  <div class="flex flex-col w-full items-center">
    <div class="flex items-center gap-3 p-1 bg-gray-300 rounded-full font-semibold mb-4">
      <span :class="{'bg-white': selected_type == 1}" class="rounded-full transition-all p-2 cursor-pointer" @click="selectType" id="1">Choose dates</span>
      <span :class="{'bg-white': selected_type == 2}" class="rounded-full transition-all p-2 cursor-pointer" @click="selectType" id="2">I'm flexible</span>
    </div>
    <DatePicker range v-model="date_range" open @change="emitDateInput()" v-if="selected_type == 1"/>
  </div>
</template>

<script>
import DatePicker from 'vue2-datepicker';
import 'vue2-datepicker/index.css';

export default {
  components:{
    DatePicker
  },
  computed:{
    selected_date(){
      let check_in_month = new Date(this.date_range[0]).toLocaleString('default', { month: 'long' }).substring(0, 3);
      let check_in_day = new Date(this.date_range[0]).getDate()
      let check_out_month = new Date(this.date_range[1]).toLocaleString('default', { month: 'long' }).substring(0, 3);
      let check_out_day = new Date(this.date_range[1]).getDate()

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
      date_range: [],

      selected_type: 1
    }
  },
  methods:{
    emitDateInput(){
      console.log(this.selected_date);
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