<template>
  <div>
    <component :is="currentComponent"></component>
    <v-bottom-navigation
      v-model="bottomNav"
      dark
      absolute
    >
      <v-btn v-for="tab in tabs" :to="tab.to" :key="tab.title" >
        <span>{{ tab.title }}</span>
        <v-icon>{{ tab.icon }}</v-icon>
      </v-btn>
    </v-bottom-navigation>
  </div>
</template>
<script>
import _ from 'lodash'
export default {
  name: 'bottom-navigation',
  data () {
    return {
      bottomNav: -1
    }
  },
  props: {
    tabs: { type: Array, require: true }
  },
  mounted () {
    // Loads on navigation, populate the correct data
    this.bottomNav = _.findIndex(this.tabs, {
      to: this.$route.fullPath
    })
  },
  computed: {
    currentComponent () {
      // Get the current tab
      return this.tabs[this.bottomNav] && this.tabs[this.bottomNav].component
    }
  }
}
</script>
