<template>
  <div id="app">
    <h1 style="text-align: center">SS-Vue-Date-Time-Range-Picker</h1>
    <div style="display: flex; justify-content: space-around;">
      <div>
        <h2>Modal-range-mode(default)</h2>
        <ss-date-time-picker
          v-model="choosenDate"
          :active.sync="datePickerIsVisible"
        ></ss-date-time-picker>
        <input type="text" id="modal-date-picker" @focus="showDatePicker" :value="inputText">
      </div>
      <div>
        <h2>Inline-range-mode</h2>
        <ss-date-time-picker
          :id=1
          :active=true
          :is-modal=false
        ></ss-date-time-picker>
      </div>
      <div>
        <h2>Inline-single-mode</h2>
        <ss-date-time-picker
          :id=2
          :active=true
          :is-modal=false
          :single-mode=true
        ></ss-date-time-picker>
      </div>
    </div>
  </div>
</template>

<script src="https://cdnjs.cloudflare.com/ajax/libs/moment.js/2.22.2/moment.min.js"></script>
<script>
import VueDateTimePicker from 'ss-vue-datetime-range-picker';
require('ss-vue-datetime-range-picker/dist/ss-vue-datetime-range-picker.css');

export default {
  name: 'App',
  components: {
    'ss-date-time-picker': VueDateTimePicker,
  },
  data() {
    return {
      datePickerIsVisible: false,
      choosenDate: {},
    };
  },
  computed: {
    inputText() {
      if (Object.keys(this.choosenDate).length !== 0) {
        return moment(this.choosenDate.fromTs * 1000).utc().format('DD.MM.YYYY hh:mm') + '-'
        + moment(this.choosenDate.toTs * 1000).utc().format('DD.MM.YYYY hh:mm');
      }

      return '';
    },
  },
  methods: {
    showDatePicker() {
      this.datePickerIsVisible = true;
    },
  },
};
</script>

<style>
</style>
