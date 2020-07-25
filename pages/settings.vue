<template>
  <v-layout>
    <div>
      <v-card class="mx-auto" style="max-width: 400px;">
          <v-card-text>
              <v-switch v-model="darkmode" class="ma-4" label="Dark Mode"></v-switch>
          </v-card-text>
      </v-card>
    </div>
  </v-layout>
</template>
<script>

export default {
  data () {
    return {
      darkmode: true
    }
  },
  mounted () {
    this.darkmode = JSON.parse(localStorage.getItem('settings')).darkmode || false
  },
  head () {
    return {
      title: 'settings',
      meta: [{
        hid: 'description',
        name: 'description',
        content: ''
      }]
    }
  },
  watch: {
    darkmode (data) {
      this.$vuetify.theme.dark = data
      localStorage.setItem('settings', JSON.stringify({ darkmode: data }))
    }
  }
}
</script>
<style>
.code-snippet {
  color: #fff;
}
</style>
