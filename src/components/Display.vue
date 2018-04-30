<template>
  <div class="haft" :style="`background: ${display.bg}; color: ${display.color};`">
    <h1>{{type}}</h1>
    <img :src="`/static/${display.icon}`" alt="" width="100px">
    <h1>{{config[type].city}} {{displayTime}}</h1>
  </div>
</template>

<script>
import { DateTime } from 'luxon'

export default {
  data () {
    return {
      config: {
        leia: {
          wakeup: 8,
          sleep: 21,
          icon: 'leia.svg',
          city: 'Bangkok'
        },
        papa: {
          wakeup: 8,
          sleep: 24,
          icon: 'papa.svg',
          city: 'San Jose'
        }
      }
    }
  },
  props: ['time', 'type'],
  computed: {
    displayTime () {
      return this.time && this.time.toLocaleString(DateTime.TIME_SIMPLE)
    },
    calTime () {
      return this.time && this.time.toFormat('H')
    },
    display () {
      if (this.calTime >= this.config[this.type].wakeup && this.calTime <= this.config[this.type].sleep) {
        return {
          bg: '#fff',
          color: '#333',
          icon: this.config[this.type].icon
        }
      } else {
        return {
          bg: '#000',
          color: '#eee',
          icon: 'sleep.svg'
        }
      }
    }
  }
}
</script>

<style scoped>
.haft {
  height: 50vh;
  text-align: center;
}
</style>
