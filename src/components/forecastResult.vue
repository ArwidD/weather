<script setup>
import wc from '@/assets/data/weatherCodes.json'
import { ref } from 'vue'
const props = defineProps(['forecast'])

const weatherCodes = ref(wc)

function getText(code) {
  let wcText =
    weatherCodes.value.find((itm) => {
      return itm.code == code
    }).description ?? 'Unknown'

  return wcText
}
</script>
<template>
  <ul>
    <li>Date</li>
    <li>Code</li>
    <li>Temp</li>
    <li>Precip</li>
    <li>Wind</li>
  </ul>
  <ul v-for="day in props.forecast.weather" :key="day">
    <li>{{ new Date(day.date).getDate() }}.{{ new Date(day.date).getMonth() + 1 }}</li>
    <li>{{ getText(day.code) }}</li>
    <li>{{ day.temp.min }} - {{ day.temp.max }}{{ day.temp.unit }}</li>
    <li>
      {{ day.precipitation.sum }}{{ day.precipitation.unit }}<br />
      {{ day.precipitation.probability }}%
    </li>
    <li>
      {{ day.wind.speed }}({{ day.wind.gusts }}){{ day.wind.unit }}<br />
      {{ day.wind.direction }}{{ day.wind.direction_unit }}
    </li>
  </ul>
</template>
<style scoped>
ul {
  padding: 0;
  display: grid;
  grid-template-columns: 12% 12% 22% 15% auto;
  margin: 0.35rem 0; /* space between rows so rounded corners are visible */
  border-radius: 8px; /* rounded corners */
  overflow: hidden; /* clip children (for rounded corners) */
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.08);
}
ul:nth-child(even) {
  background-color: rgb(111, 121, 168);
}
ul:nth-child(odd) {
  background-color: rgba(46, 47, 99, 0.582);
}
li {
  padding: 0 0.5em;
  list-style-type: none;
  vertical-align: top;
}
</style>
