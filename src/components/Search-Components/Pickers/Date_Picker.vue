<template>
  <div>
    <DatePicker range v-model="date_range" @change="emitDateInput()"/>
    {{selected_date}}
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
      date_range: []
    }
  },
  methods:{
    emitDateInput(){
      console.log('input date');
      this.$emit('dateInput', this.selected_date)
    }
  }
}
</script>

<style>
</style>