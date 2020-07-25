<template>
  <v-card class="color-wrap">
    <v-color-picker v-model="color"></v-color-picker>
    <div id="color-select" class="pa-4">
      <v-select
        :items="types"
        label="Output Format"
        outlined
        v-model="type"
      ></v-select>
    </div>
      <v-sheet
        dark
        class="pa-4"
      >
        <pre>Output: {{ showColor }}</pre>
      </v-sheet>
  </v-card>
</template>
<script>
export default {
  data: () => ({
    types: ['hex', 'hexa', 'rgba', 'hsla', 'hsva'],
    type: 'hex',
    hex: '#FF00FF',
    hexa: '#FF00FFFF',
    rgba: { r: 255, g: 0, b: 255, a: 1 },
    hsla: { h: 300, s: 1, l: 0.5, a: 1 },
    hsva: { h: 300, s: 1, v: 1, a: 1 }
  }),
  computed: {
    color: {
      get () {
        return this[this.type]
      },
      set (v) {
        this[this.type] = v
      }
    },
    showColor () {
      if (typeof this.color === 'string') {
        return this.color
      }

      return JSON.stringify(Object.keys(this.color).reduce((color, key) => {
        color[key] = Number(this.color[key].toFixed(2))
        return color
      }, {}), null, 2)
    }
  }
}
</script>
<style>
.color-wrap {
  max-width: 300px;
}

#color-select {
  width: 100%;
}
</style>
