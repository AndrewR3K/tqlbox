<template>
    <div>
        <v-card-title>Full Screen iFrame Embed</v-card-title>
        <v-card-text>
            <v-text-field label="Another input" v-model="embed"></v-text-field>
            <div v-show="generated">
            Code Snippet:
            <div ref="textToCopy" class="code-snippet">{{embedcode}}</div>
            </div>
        </v-card-text>
        <v-card-actions>
            <v-btn
            text
            color="accent"
            @click="generateCode"
            >
            Generate Code
            </v-btn>
        </v-card-actions>
    </div>
</template>
<script>

export default {
  data () {
    return {
      embed: null,
      generated: false
    }
  },
  computed: {
    embedcode () {
      return `<iframe src="${this.embed}" style="width: 100vw; height: 100vh"></iframe>`
    }
  },
  methods: {
    generateCode () {
      if (this.embed) {
        this.generated = true
        this.copyText()
      }
    },
    copyText () {
      navigator.clipboard.writeText(this.embedcode)
    }
  }
}
</script>
<style>
</style>
