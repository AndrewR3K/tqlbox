<template>
  <v-layout>
    <div>
      <v-card class="mx-auto" style="max-width: 400px;">
        <Iframe />
      </v-card>
    </div>
  </v-layout>
</template>
<script>

export default {
  data () {
    return {
      embed: null,
      generated: false
    }
  },
  head () {
    return {
      title: 'embedables',
      meta: [{
        hid: 'description',
        name: 'description',
        content: 'My custom description'
      }]
    }
  },
  computed: {
  },
  methods: {
  }
}
</script>
<style>
.code-snippet {
  color: #fff;
}
</style>
