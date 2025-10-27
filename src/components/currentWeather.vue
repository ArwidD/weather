<script setup>
import wc from '@/assets/data/weatherCodes.json'
import { ref } from 'vue'
const props = defineProps(['weather'])
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
  <p>{{ getText(props.weather.code) }}</p>
  <ul>
    <li>Temp: {{ props.weather.temp.temp }}{{ props.weather.temp.temp_unit }}</li>
    <li>Humidity: {{ props.weather.temp.humidity }}{{ props.weather.temp.humidity_unit }}</li>
    <li>Apparent: {{ props.weather.temp.apparent }}{{ props.weather.temp.temp_unit }}</li>
  </ul>
  <ul>
    <li>
      Precipitation: {{ props.weather.precipitation.precipitation
      }}{{ props.weather.precipitation.unit }}
    </li>
    <li>cloud coverage: {{ props.weather.cloud.coverage }}{{ props.weather.cloud.unit }}</li>
    <li>Pressure: {{ props.weather.pressure.pressure }}{{ props.weather.pressure.unit }}</li>
  </ul>
  <ul>
    <li>Wind speed:{{ props.weather.wind.windspeed }}{{ props.weather.wind.unit }}</li>
    <li>Wind gusts:{{ props.weather.wind.windgusts }}{{ props.weather.wind.unit }}</li>
    <li>Direction:{{ props.weather.wind.direction }}{{ props.weather.wind.direction_unit }}</li>
  </ul>
</template>
<style scoped>
ul {
  background: var(--color-background-soft);
  margin: 0.35rem 0;
  padding: 0.25rem 0.5rem;
  border-radius: 8px;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.06);
  list-style: none;
}
li {
  padding: 0.25rem 0.5rem;
}
</style>
