<template>
<div class="row">
    <div class="card">
        <h1 class="card__header">{{ currentDayTitle }}</h1>
        <div id="days">
        <div v-for="day in daysOfWeek" :key="day" :class="['day', { 'current-day': day === currentDay, 'selected-day': day === selectedDay, 'weekend': day === 'Saturday' || day === 'Sunday' }]" @click="selectDay(day)">
        {{ day }}
        </div>
        </div>
        <div class="card__body" id="selected-day">Selected day is: {{ selectedDay }}</div>
    </div>
    <div class="card card-primary">
        <div class="card__header">Ini Header card</div>
        <div class="card__body">Ini Body card</div>
    </div>
    <div class="card">
        <div class="card__header">Lorem ipsum dolor sit amet.</div>
        <div class="card__body">Lorem ipsum dolor sit amet consectetur adipisicing elit. Tempore dolor consectetur pariatur veniam, ipsam eos expedita repellat eum, exercitationem quia tempora, repellendus debitis aut et temporibus voluptatem molestiae corporis at! Nam architecto in quo soluta odit. Doloremque odit nihil debitis, necessitatibus laudantium officiis. Distinctio deleniti laborum blanditiis enim recusandae? Sint!</div>
    </div>
</div>
</template>
<script>
export default {
  data() {
    return {
      daysOfWeek: [
        "Sunday",
        "Monday",
        "Tuesday",
        "Wednesday",
        "Thursday",
        "Friday",
        "Saturday",
      ],
      currentDay: "",
      currentDayTitle: "",
      selectedDay: ""
    };
  },
  mounted() {
    this.currentDay = this.getCurrentDay();
    this.currentDayTitle = "Today is " + this.currentDay;
  },
  methods: {
    getCurrentDay() {
      const days = [
        "Sunday",
        "Monday",
        "Tuesday",
        "Wednesday",
        "Thursday",
        "Friday",
        "Saturday"
      ];
      const today = new Date().getDay();
      return days[today];
    },
    selectDay(day) {
      this.selectedDay = day;
    }
  }
};
</script>
<style scoped>
.day {
  display: inline-block;
  margin-top: 0.375rem;
  width: 100px;
  margin-right: 10px;
  border: 1px solid transparent;
  border-radius: 0.375rem;
  text-align: center;
  line-height: 50px;
  cursor: pointer;
  background-color: #8a1ee2;
  color: #ffffff;
  transition: border-color 0.25s;
  /* box-shadow: 0px 10px 38px -3px rgba(0,0,0,0.1); */
}
.day:hover {
    border-color: #0E2954;
}
.day:focus,.day:focus-visible {
    outline: 4px auto -webkit-focus-ring-color;
}
#days {
    background-color: #FF78C4;
    padding: 1rem;
    border-radius: 0.75rem;
}
.current-day {
  background-color: green;
  color: #e9e9e9;
}
.weekend{
 background-color: #a51b1b;
}
.selected-day {
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.5);
  outline: 2px solid white;
  background-color: #0E2954;
}
</style>