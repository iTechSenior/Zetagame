<template>
  <v-toolbar id="core-toolbar" color="black">
    <v-toolbar-items>
      <router-link :to="'/account-management'">
        <v-btn flat>
          <v-icon>mdi-home</v-icon>
        </v-btn>
      </router-link>
      <router-link v-for="(link, i) in links" :key="i" :to="link.to">
        <v-btn flat>
          <v-icon>{{ link.icon }}</v-icon>
          {{ link.text }}
        </v-btn>
      </router-link>
    </v-toolbar-items>
  </v-toolbar>
</template>

<script>
// Utilities
import { mapMutations, mapState } from 'vuex'

export default {
  data: () => ({
    logo: './img/logo.png',
    links: [
      {
        to: '/sports-betting',
        icon: '',
        text: 'Sports Betting'
      },
      {
        to: '/live-bet',
        icon: '',
        text: 'Live Bet'
      },
      {
        to: '/casino',
        icon: '',
        text: 'Casino'
      },
      {
        to: '/live-casino',
        icon: '',
        text: 'Live Casino'
      },
      {
        to: '/virtual-games',
        icon: '',
        text: 'Virtual Games'
      }
    ],
    responsive: false
  }),
  computed: {
    ...mapState('app', ['image', 'color']),
    inputValue: {
      get() {
        return this.$store.state.app.drawer
      },
      set(val) {
        this.setDrawer(val)
      }
    },
    items() {
      return this.$t('Layout.View.items')
    }
  },
  mounted() {
    this.onResponsiveInverted()
    window.addEventListener('resize', this.onResponsiveInverted)
  },
  beforeDestroy() {
    window.removeEventListener('resize', this.onResponsiveInverted)
  },
  methods: {
    ...mapMutations('app', ['setDrawer', 'toggleDrawer']),
    onResponsiveInverted() {
      if (window.innerWidth < 991) {
        this.responsive = true
      } else {
        this.responsive = false
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.v-toolbar {
  margin-top: 92px;
}
</style>
