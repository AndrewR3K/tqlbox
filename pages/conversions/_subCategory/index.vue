<template>
  <div>
    <bottom-navigation :tabs="tabs" />
  </div>
</template>
<script>
export default {
  data () {
    return {
      tabs: [
        // {
        //   icon: 'mdi-beaker',
        //   title: 'Units',
        //   to: '/conversions/units',
        //   component: () => import(`../../../components/units.vue`)
        // },
        {
          icon: 'mdi-map-clock',
          title: 'Time Zones',
          to: '/conversions/time-zones',
          component: () => import(`../../../components/time-zones.vue`)
        }
      ]
    }
  }
}
</script>
