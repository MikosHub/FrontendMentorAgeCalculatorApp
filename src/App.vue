<template>
  <div id="container">
    <div id="dateFilters">
      <label for="dayInput">Day
        <input type="text" id="dayInput" v-model="day">
      </label>
      <label for="monthInput">Month
        <input type="text" id="monthInput" v-model="month">
      </label>
      <label for="yearInput">Year
        <input type="text" id="yearInput" v-model="year">
      </label>
    </div>
    <div id="buttonRow">
      <button @click.prevent="onCalculateButtonClicked"><img src="./assets/icon-arrow.svg" alt="Calculate"></button></div>
    <div id="resultDisplay">
      <ResultRow :value="resultYears" :text="'years'"></ResultRow>
      <ResultRow :value="resultMonths" :text="'months'"></ResultRow>
      <ResultRow :value="resultDays" :text="'days'"></ResultRow>
    </div>
  </div>
</template>

<script>

import ResultRow from './components/ResultRow.vue';
import DateTimeDifference from 'datetime-difference';

export default {
  data() {
    return {
      day: '',
      month: '',
      year: '',
      resultDays: '--',
      resultMonths: '--',
      resultYears: '--'
    }
  },
  components: { ResultRow },
  methods: {
    onCalculateButtonClicked() {
      console.log(`day: ${this.day}, month: ${this.month}, year: ${this.year}`);

      // TODO Validation stuff

      const day = parseInt(this.day);
      const month = parseInt(this.month);
      const year = parseInt(this.year);

      const date = new Date(year, month-1, day);
      const now = new Date();

      const diff = DateTimeDifference(now, date);

      this.resultDays = diff.days;
      this.resultMonths = diff.months;
      this.resultYears = diff.years;
    }
  }
}

</script>