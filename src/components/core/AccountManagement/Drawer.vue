<template>
  <v-navigation-drawer id="app-drawer" v-model="inputValue">
    <v-layout class="fill-height" tag="v-list" column>
      <v-list-tile
        v-for="(panel, i) in panels"
        :key="i"
        :active-class="color"
        class="v-list-item"
        @click="panelName = panel.name"
      >
        <v-list-tile-action>
          <v-icon>{{ panel.icon }}</v-icon>
        </v-list-tile-action>
        <v-list-tile-title v-text="panel.text" />
      </v-list-tile>
    </v-layout>
  </v-navigation-drawer>
</template>

<script>
// Utilities
import { mapMutations, mapState } from 'vuex'

export default {
  data: () => ({
    logo: './img/logo.png',
    currentPanel: '',
    panels: [
      {
        name: 'core-account-management-panel-my-bets',
        icon: 'mdi-calendar',
        text: 'My Bets'
      },
      {
        name: 'core-account-management-panel-account-activities',
        icon: 'mdi-account',
        text: 'Account Activities'
      },
      {
        name: 'core-account-management-panel-user-list',
        icon: 'mdi-account-group',
        text: 'User List'
      },
      {
        name: 'core-account-management-panel-user-balance',
        icon: 'mdi-account-group',
        text: 'User Balance'
      },
      {
        name: 'core-account-management-panel-income-expense',
        icon: 'mdi-cash-multiple',
        text: 'Income / Expense'
      },
      {
        name: 'core-account-management-panel-printer-settings',
        icon: 'mdi-printer-settings',
        text: 'Printer Settings'
      },
      {
        name: 'core-account-management-panel-change-password',
        icon: 'mdi-key-variant',
        text: 'Change Password'
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

<style lang="scss">
#app-drawer {
  .v-list__tile {
    border-radius: 4px;

    &--buy {
      margin-top: auto;
      margin-bottom: 17px;
    }
  }

  .v-image__image--contain {
    top: 9px;
    height: 60%;
  }

  .search-input {
    margin-bottom: 30px !important;
    padding-left: 15px;
    padding-right: 15px;
  }
}
</style>
