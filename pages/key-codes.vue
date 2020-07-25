<template>
  <v-layout >
    <div>
        <v-card class="mx-auto" style="max-width: 400px;">
            <v-card-title>Press a key on your keyboard to see its code.</v-card-title>
            <v-card-text v-if="keypressed" class="keypress" style="text-align: left; padding-top: 10px;">
                <div class="display-1"><small>Key:</small> <span style="color:var(--su-color);">{{keypressed.key}}</span></div>
                <div class="display-1"><small>Char Code:</small> <span style="color:var(--su-color)">{{keypressed.char_code}}</span></div>
                <div class="display-1"><small>Key Code:</small> <span style="color:var(--su-color);">{{keypressed.key_code}}</span></div>
            </v-card-text>
        </v-card>
    </div>
  </v-layout>
</template>
<script>

export default {
  data () {
    return {
      embed: null,
      generated: false,
      keypressed: null
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
  mounted () {
    document.addEventListener('keypress', this.storeKey)
  },
  beforeDestroy () {
    document.removeEventListener('keypress', this.storeKey)
  },
  computed: {
  },
  methods: {
    storeKey (event) {
      this.keypressed = {
        char_code: event.charCode,
        key_code: event.keyCode,
        key: event.key,
        shift_key: event.shift_key
      }
    }
  }
}
</script>
<style>
.code-snippet {
  color: #fff;
}
</style>
