<template>
  <div class="hello">
    <display :time="leia" type="leia"></display>
    <display :time="papa" type="papa"></display>
  </div>
</template>

<script>
import { DateTime } from 'luxon'
import Display from './Display'

export default {
  name: 'HelloWorld',
  components: {
    Display
  },
  created () {
    setInterval(() => {
      let local = DateTime.local()
      this.leia = local.setZone('UTC+7')
      this.papa = local.setZone('UTC-7')
    }, 1000)
  },
  data () {
    return {
      leia: null,
      papa: null
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
