<template>
  <div id="app">
    <div class="container">



    <div class="dropdown">
      <button class="btn btn-primary dropdown-toggle" type="button" data-toggle="dropdown">
        {{ this.monthYearLabel }}
        <span class="caret"></span>
      </button>
      <ul class="dropdown-menu scrollable-menu">
        <li v-for="month in months" @click="setMonthYear(month)">
          <a href="#">{{ month.format('MMM, YYYY') }}</a>
        </li>
      </ul>
    </div>

    <div class="dropdown">
      <button class="btn btn-primary dropdown-toggle" type="button" data-toggle="dropdown">
        {{ this.dayLabel }}
        <span class="caret"></span>
      </button>
      <ul class="dropdown-menu scrollable-menu">
        <li v-for="day in days" @click="setDay(day)">
          <a href="#">{{ day }}</a>
        </li>
      </ul>
    </div>

    <div class="input-append date form_datetime">
        <input class="form" size="16" type="text" :value="this.date" readonly>
        <span class="add-on"><i class="icon-th"></i></span>
    </div>


    </div>
  </div>
</template>

<script>
import moment from 'moment';

export default {
  data() {
    return {
      monthYearLabel: moment().format('MMM, YYYY'),
      dayLabel: moment().format('D'),
      moment: moment(),
      months: [],
      days: ["please select a month"],
      numberOfDays: 0,
      date: "MM/DD/YYYY",
      selectedDay: "",
      selectedMonthYear: {}
    }
  },
  beforeMount() {
    for (var i = 12; i >= 1; i--) {
      this.months.push(this.moment.clone().subtract(i, 'M'));
    }
    for (var i = 0; i <= 12; i++) {
      this.months.push(this.moment.clone().add(i, 'M'));
    }
  },
  methods: {
    setMonthYear(month) {
      this.days = [];
      this.numberOfDays = month.daysInMonth();
      // limits the range of days as to not exceed one year ago
      if (month.format('MMM, YYYY') ===
          moment().subtract(1, 'year').format('MMM, YYYY')) {
        var startDay = moment().format('d');
        for (var i = startDay; i <= this.numberOfDays; i++) {
          this.days.push(i.toString());
        }
        // limits the range of days as to not exceed one year from now
      } else if (month.format('MMM, YYYY') ===
                 moment().add(1, 'year').format('MMM, YYYY')) {
          var endDay = moment().format('d');
          for (var i = 1; i <= endDay; i++) {
            this.days.push(i.toString());
          }
      // handles all other in-between cases
      } else {
        for (var i = 1; i <= this.numberOfDays; i++) {
          this.days.push(i.toString());
        }
      }
      this.selectedMonthYear = month;
      this.date = month.format('MM/DD/YYYY');
      this.monthYearLabel = month.format('MMM, YYYY');
    },
    setDay(day) {
      this.selectedDay = day;
      if (this.selectedDay != "" && this.selectedMonthYear != {}) {
        this.date = this.selectedMonthYear.startOf('month').add(day - 1, 'd').format('MM/DD/YYYY');
      }
      this.dayLabel = day;
    }
  }
}
</script>

<style>

  .container {
    padding-top: 50px;
    width: 500px;
    margin: 0 auto;
  }

  button {
    width: 130px;
  }

  .dropdown, .date {
    display: inline;
  }

  .form {
    width: 200px;
    padding-left: 10px;
  }

  li {
    padding-left: 10px;
  }

  .scrollable-menu {
      height: auto;
      max-height: 250px;
      overflow-x: hidden;
  }
</style>
