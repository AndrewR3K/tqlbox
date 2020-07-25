<template>
  <v-app dark :style="cssProps">
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      mobile-breakpoint=500
      app
    >
      <div class="logo-wrap">
        <Logo class="logo" />
        <h1>{{title}}</h1>
      </div>
      <v-list>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <!-- <v-app-bar
      :clipped-left="clipped"
      fixed
      app
    >
    <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
    <v-toolbar-title v-text="title" />
    </v-app-bar> -->
    <v-content>
      <Github />
      <div class="app-content">
        <nuxt />
      </div>
    </v-content>
    <v-footer
      :absolute="!fixed"
      app
    >
      <span>&copy; {{ new Date().getFullYear() }}</span>
      <span class="madeby">Made with <v-icon class="love-icon">{{love}}</v-icon> in San Jose, CA</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      clipped: false,
      drawer: true,
      fixed: false,
      love: 'mdi-cards-heart',
      items: [
        {
          icon: 'mdi-apps',
          title: 'Home',
          to: '/'
        },
        {
          icon: 'mdi-share-variant',
          title: 'Embedables',
          to: '/embedables'
        },
        {
          icon: 'mdi-keyboard',
          title: 'Key Codes',
          to: '/key-codes'
        },
        {
          icon: 'mdi-brush',
          title: 'Color Picker',
          to: '/color-picker'
        },
        {
          icon: 'mdi-cog',
          title: 'Settings',
          to: '/settings'
        }
      ],
      miniVariant: false,
      title: 'TQLBox'
    }
  },
  mounted  () {
    if (localStorage.getItem('settings')) {
      this.$vuetify.theme.dark = JSON.parse(localStorage.getItem('settings')).darkmode
    }
  },
  computed: {
    cssProps () {
      return {
        '--p-color': this.$vuetify.theme.currentTheme.primary,
        '--a-color': this.$vuetify.theme.currentTheme.accent,
        '--s-color': this.$vuetify.theme.currentTheme.secondary,
        '--i-color': this.$vuetify.theme.currentTheme.info,
        '--w-color': this.$vuetify.theme.currentTheme.warning,
        '--e-color': this.$vuetify.theme.currentTheme.error,
        '--su-color': this.$vuetify.theme.currentTheme.success
      }
    }
  }
}
</script>
<style>

.app-content {
  margin: 20px;
  word-wrap: normal;
  word-break: keep-all;
  /* padding-top: 20px; */
}

.v-card, .v-card__title {
  word-break: keep-all !important;
}

.logo-wrap {
  width: 120px;
  margin: 0 auto;
  text-align: center;
  margin-top: 20px;
  margin-bottom: 20px;
}

h1 {
  font-weight: 700;
  font-size: 30px;
}

.madeby {
  margin-left: 20px;
}

.love-icon.v-icon{
  color: var(--e-color) !important;
}

@media (max-width: 850px) {
  .app-content {
    margin-right: 80px;
  }
}
</style>
