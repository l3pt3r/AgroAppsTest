<script>
import moment from 'moment'

// defineProps({
//   days: {
//     type: Object,
//     required: true
//   }
// })

export default {
  props: {
    days: {
      type: Object,
      required: true
    }
  },
  methods: {
    changeDay(d) {
      this.$emit('changeDay', d)
    }
  }
}
</script>

<template>
  <h3>7-day Forecast</h3>
  <div class="list">
    <div class="dayDetails" v-for="day in days" @click="changeDay(day)">
      <!-- <label>{{ moment(day.dt).format('dddd') }} </label> -->
      <label style="font-weight: bold;">{{ day.temp.day }} &deg;C</label>
      <label>{{ day.weather[0].description }}</label>
    </div>
  </div>
</template>

<style scoped>
h1,
h2,
h3,
label {
  color: navy;
}

.list {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
}

.dayDetails {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  margin: 1em 1em;
  padding: 1em;
  background-color: rgba(240, 240, 240, 0.1);
  box-shadow: rgba(255, 255, 255, 0.76) 0px 22px 70px 4px;
  border-radius: 1rem;
  border: 2px solid navy;
  width: 20em;
  height: 7em;
}

@media (max-width: 1024px) {
    h3 {
      margin-top: 2rem;
      text-align: center;
    }
    .list {
        flex-direction: column;
        /* margin: 5rem 1rem; */
    }
}
</style>
