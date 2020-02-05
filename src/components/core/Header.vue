<template>
  <div class="header">
    <material-logo :logourl="logourl" />
    <core-header-login />
    <core-header-Deposit />
    <core-header-Menu />
  </div>
</template>
<script>
import { mapMutations } from 'vuex'

export default {
  data: () => ({
    notifications: [
      'Mike, John responded to your email',
      'You have 5 new tasks',
      "You're now a friend with Andrew",
      'Another Notification',
      'Another One'
    ],
    title: null,
    responsive: false,
    responsiveInput: false,
    logourl: 'img/logo.png'
  }),

  watch: {
    $route(val) {
      this.title = val.name
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
    onClickBtn() {
      this.setDrawer(!this.$store.state.app.drawer)
    },
    onClick() {
      //
    },
    onResponsiveInverted() {
      if (window.innerWidth < 991) {
        this.responsive = true
        this.responsiveInput = false
      } else {
        this.responsive = false
        this.responsiveInput = true
      }
    }
  }
}
</script>

<style>
#core-toolbar a {
  text-decoration: none;
}
.header {
  background-color: black;
}
.header .logo {
  top: 20px;
  left: 20px;
}
</style>
