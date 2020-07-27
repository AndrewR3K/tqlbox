<template>
  <div>
    <v-card style="max-width: 290px;">
      <v-card-title>Current Time</v-card-title>
      <v-card-subtitle>Click on the clock to begin converting!</v-card-subtitle>
       <v-time-picker
          v-model="picker"
          flat
        ></v-time-picker>
    </v-card>
    <v-card style="max-width: 290px;" class="mt-5">
      <v-card-title>Converted Time</v-card-title>
      <v-card-content>
        <div class="pa-5 pb-0">
          <v-select
            v-model="tz"
            :items="timezones"
            label="Select a time zone"
            outlined
          />
        </div>
        <v-card-text style="text-align: right;">
            <span class="time-output">{{convertedTime.time}}</span><span class="time-a">{{convertedTime.a}}</span>
        </v-card-text>
      </v-card-content>
    </v-card>
  </div>
</template>
<script>
import moment from 'moment-timezone'
export default {
  data () {
    return {
      picker: moment().format('HH:mm'),
      tz: moment.tz.guess()
    }
  },
  computed: {
    convertedTime () {
      const cnvt = moment(this.picker, 'HH:mm').tz(this.tz)
      return {
        time: cnvt.format('hh:mm'),
        a: cnvt.format('a')
      }
    },
    timezones () {
      return moment.tz.names()
    }
  }
}
</script>
<style>
.time-output {
  font-size: 70px;
}

.time-a {
  font-size: 16px;
  text-transform: uppercase;
}
</style>
