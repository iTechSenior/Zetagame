<template>
  <v-app dark>
    <core-header />
    <v-content>
      <div id="core-view">
        <v-fade-transition mode="out-in">
          <v-container fluid style="height:100%">
            <v-layout
              row
              class="pa-2"
              style="background-color: green; font-size: 16px; color: white; font-weight:bold;"
            >
              <v-container
                class="ma-0 pa-0 pl-3"
                style="width: 300px !important; max-width: 300px;"
                >Account Management</v-container
              >
              <v-container class="ma-0 pa-0 pl-3">{{
                currentPanel.text
              }}</v-container>
            </v-layout>
            <v-layout row style="height: calc(100% - 40px);">
              <v-navigation-drawer
                id="app-drawer"
                v-model="inputValue"
                width="360"
                floating
                persistent
                style="min-width: 300px;"
              >
                <v-img height="100%">
                  <v-layout class="fill-height" tag="v-list" column>
                    <v-list-tile
                      v-for="(panel, i) in panels"
                      :key="i"
                      :active-class="color"
                      :to="panel.id"
                      class="v-list-item"
                      @click="drawerClick($event, panel)"
                    >
                      <v-list-tile-action>
                        <v-icon>{{ panel.icon }}</v-icon>
                      </v-list-tile-action>
                      <v-list-tile-title v-text="panel.text" />
                    </v-list-tile>
                  </v-layout>
                </v-img>
              </v-navigation-drawer>
              <component :is="currentPanel.name"></component>
            </v-layout>
          </v-container>
        </v-fade-transition>
      </div>
    </v-content>
    <core-footer />
  </v-app>
</template>

<script>
import { mapMutations, mapState } from 'vuex'
export default {
  data() {
    return {
      currentPanel: {
        name: 'core-account-management-panel-my-bets',
        id: '#p_mybets',
        icon: 'mdi-calendar',
        text: 'My Bets'
      },
      panels: [
        {
          name: 'core-account-management-panel-my-bets',
          id: '#p_mybets',
          icon: 'mdi-calendar',
          text: 'My Bets'
        },
        {
          name: 'core-account-management-panel-account-activities',
          id: '#p_activities',
          icon: 'mdi-account',
          text: 'Account Activities'
        },
        {
          name: 'core-account-management-panel-user-list',
          id: '#p_users',
          icon: 'mdi-format-list-bulleted',
          text: 'User List'
        },
        {
          name: 'core-account-management-panel-user-balance',
          id: '#p_userBalance',
          icon: 'mdi-wallet',
          text: 'User Balance'
        },
        {
          name: 'core-account-management-panel-income-expense',
          id: '#p_income',
          icon: 'mdi-cash-multiple',
          text: 'Income / Expense'
        },
        {
          name: 'core-account-management-panel-printer-settings',
          id: '#p_printer',
          icon: 'mdi-printer-settings',
          text: 'Printer Settings'
        },
        {
          name: 'core-account-management-panel-change-password',
          id: '#p_chpwd',
          icon: 'mdi-key-variant',
          text: 'Change Password'
        }
      ],
      responsive: false
    }
  },

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
        this.responsive = false
      } else {
        this.responsive = false
      }
    },
    drawerClick(event, panel) {
      this.currentPanel = panel
      let element = event.path[2]
      let vLst = document.getElementsByClassName('v-list-item')
      Array.prototype.forEach.call(vLst, element => {
        element.style.backgroundColor = '#272727'
      })
      if (!element.classList.contains('v-list-item')) element = event.path[1]
      element.style.backgroundColor = 'rgba(200, 200, 200, 0.2)'
    }
  }
}
</script>

<style>
#core-view {
  height: 100%;
}
</style>
