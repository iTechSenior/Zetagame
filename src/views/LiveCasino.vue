<template>
  <v-app dark>
    <core-header />
    <v-content>
      <div id="core-view" style="background-color: black;">
        <v-fade-transition mode="out-in">
          <v-container style="max-width: 90%;" class="livecasino">
            <v-layout style="position: relative;">
              <v-carousel height="600" hide-delimiters>
                <v-carousel-item
                  v-for="(item, i) in carousel"
                  :key="i"
                  :src="item.src"
                ></v-carousel-item>
              </v-carousel>

              <span
                style="position: absolute; right: 200px; bottom: 200px; background-color: rgba(0,0,0,.6); box-shadow: 0px 0px 20px 20px rgba(0,0,0,.6);"
              >
                <span
                  style="font-size: 50px; text-transform: uppercase; line-height: 1.2; font-weight: bold;"
                >
                  Exciting
                  <span style="color: #4caf50;">Live</span>
                  <br />Table Games
                </span>
                <br />
                <span style="font-size: 24px;">From Top Providers</span>
              </span>
            </v-layout>
            <v-layout>
              <v-container
                style="margin-top: -120px; z-index: 100; max-width: 95%;"
              >
                <v-layout>
                  <v-flex xs3 class="left-menu mr-3">
                    <v-list class="pa-0">
                      <v-list-tile>
                        <v-icon
                          style="position: absolute; background-color: green; width: 74px; height: 74px; top: 0; left: 0; font-size: 50px;"
                          >mdi-magnify</v-icon
                        >

                        <v-list-tile-content
                          style="margin-left: 74px;"
                          class="mt-2"
                        >
                          <v-text-field
                            hide-details
                            append-icon="mdi-magnify"
                          ></v-text-field>
                        </v-list-tile-content>
                      </v-list-tile>
                      <v-divider></v-divider>
                      <v-list-tile>
                        <span>
                          <img src="/img/poker_token.png" alt="All Games" />
                        </span>

                        <v-list-tile-content class="ml-3"
                          >All Games</v-list-tile-content
                        >
                      </v-list-tile>
                      <v-divider></v-divider>
                      <v-list-tile>
                        <span>
                          <img src="/img/roulette.png" alt="Roulette" />
                        </span>

                        <v-list-tile-content class="ml-3"
                          >Roulette</v-list-tile-content
                        >
                      </v-list-tile>
                      <v-divider></v-divider>
                      <v-list-tile>
                        <span>
                          <img src="/img/blackjack.png" alt="Blackjack" />
                        </span>
                        <v-list-tile-content class="ml-3"
                          >Blackjack</v-list-tile-content
                        >
                      </v-list-tile>
                      <v-divider></v-divider>
                      <v-list-tile>
                        <span>
                          <img src="/img/joker_card.png" alt="Jokercard" />
                        </span>
                        <v-list-tile-content class="ml-3"
                          >Casino Holdem</v-list-tile-content
                        >
                      </v-list-tile>
                      <v-divider></v-divider>
                      <v-list-tile>
                        <span>
                          <img src="/img/three_cards.png" alt="Poker" />
                        </span>

                        <v-list-tile-content class="ml-3"
                          >Poker</v-list-tile-content
                        >
                      </v-list-tile>
                    </v-list>
                  </v-flex>
                  <v-flex xs9>
                    <v-layout class="mid-menu">
                      <v-btn-toggle v-model="toggle_providers" mandatory>
                        <v-btn flat>All</v-btn>
                        <v-btn flat style="text-align: center;">
                          <img src="/img/ezugi.png" />
                        </v-btn>
                        <v-btn flat>
                          <img src="/img/logos/providers/evolution.png" />
                        </v-btn>
                        <v-btn flat>
                          <img
                            src="/img/logos/providers/luckystreak.png"
                            height="35"
                          />
                        </v-btn>
                      </v-btn-toggle>
                    </v-layout>

                    <v-layout style="flex-wrap: wrap;">
                      <v-flex
                        v-for="(game, index) in livegames"
                        :key="index"
                        style="width: 33.33%; float: left;"
                        class="pa-1"
                      >
                        <v-card style="position: relative;">
                          <v-img
                            :src="game.thumbnail"
                            aspect-ratio="1.2"
                          ></v-img>
                          <div
                            style="position: absolute; top: 0; width: 100%; height: 100%; background-color: rgba(48,48,48,.5)"
                          ></div>
                          <v-card-actions
                            style="position: absolute; bottom: 20px; width: 100%; font-size: 24px; justify-content: center;"
                            class="ma-0"
                          >
                            <v-chip label color="red" style="font-size: 30px;"
                              >LIVE</v-chip
                            >
                            {{ game.name }}
                          </v-card-actions>
                        </v-card>
                      </v-flex>
                    </v-layout>
                    <v-layout>
                      <v-flex xs6 style="padding-top: 11px;" class="pl-1 pr-1">
                        <v-divider
                          style="border-color: white; border-width: 1px;"
                        ></v-divider>
                      </v-flex>
                      <v-flex
                        class="text-xs-center"
                        style="font-size: 16px; width: 110px;"
                        >Other Games</v-flex
                      >
                      <v-flex xs6 style="padding-top: 11px;" class="pl-1 pr-1">
                        <v-divider
                          style="border-color: white; border-width: 1px;"
                        ></v-divider>
                      </v-flex>
                    </v-layout>
                    <v-layout style="flex-wrap: wrap;">
                      <v-flex
                        v-for="(game, index) in games"
                        :key="index"
                        style="width: 20%; min-width: 20%;"
                        class="pa-1"
                      >
                        <v-card style="position: relative;">
                          <v-img
                            :src="game.thumbnail"
                            aspect-ratio="1.2"
                          ></v-img>
                          <v-img
                            src="/img/table_games/mask.png"
                            aspect-ratio="1.2"
                            style="position: absolute; top: 0; width: 100%;"
                          ></v-img>
                          <v-card-actions>{{ game.name }}</v-card-actions>
                        </v-card>
                      </v-flex>
                    </v-layout>
                  </v-flex>
                </v-layout>
              </v-container>
            </v-layout>
          </v-container>
        </v-fade-transition>
      </div>
    </v-content>
    <core-footer />
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      carousel: [
        {
          src:
            '/img/2018_june_shangri_la_dual_play_roulette_mixed_group_shot_11.png'
        }
      ],
      toggle_providers: 0,
      livegames: [
        {
          name: 'Baccarat',
          thumbnail: '/img/table_games/live_baccarat.png'
        },
        {
          name: 'Roulette',
          thumbnail: '/img/table_games/live_roulette.png'
        },
        {
          name: 'BlackJack',
          thumbnail: '/img/table_games/live_blackjack.png'
        }
      ],

      games: [
        {
          name: 'Evolution',
          thumbnail: '/img/table_games/evolution.png'
        },
        {
          name: 'Blackjack Classic 2',
          thumbnail: '/img/table_games/blackjack.png'
        },
        {
          name: 'Evolution',
          thumbnail: '/img/table_games/evolution1.png'
        },
        {
          name: 'Private Roulette 1',
          thumbnail: '/img/table_games/private_roulette.png'
        },
        {
          name: 'Ezugi',
          thumbnail: '/img/table_games/ezugi.png'
        },
        {
          name: 'Evolution',
          thumbnail: '/img/table_games/evolution.png'
        },
        {
          name: 'Blackjack Classic 2',
          thumbnail: '/img/table_games/blackjack.png'
        },
        {
          name: 'Evolution',
          thumbnail: '/img/table_games/evolution1.png'
        },
        {
          name: 'Private Roulette 1',
          thumbnail: '/img/table_games/private_roulette.png'
        },
        {
          name: 'Ezugi',
          thumbnail: '/img/table_games/ezugi.png'
        },
        {
          name: 'Evolution',
          thumbnail: '/img/table_games/evolution.png'
        },
        {
          name: 'Blackjack Classic 2',
          thumbnail: '/img/table_games/blackjack.png'
        },
        {
          name: 'Evolution',
          thumbnail: '/img/table_games/evolution1.png'
        },
        {
          name: 'Private Roulette 1',
          thumbnail: '/img/table_games/private_roulette.png'
        },
        {
          name: 'Ezugi',
          thumbnail: '/img/table_games/ezugi.png'
        },
        {
          name: 'Evolution',
          thumbnail: '/img/table_games/evolution.png'
        },
        {
          name: 'Blackjack Classic 2',
          thumbnail: '/img/table_games/blackjack.png'
        },
        {
          name: 'Evolution',
          thumbnail: '/img/table_games/evolution1.png'
        },
        {
          name: 'Private Roulette 1',
          thumbnail: '/img/table_games/private_roulette.png'
        },
        {
          name: 'Ezugi',
          thumbnail: '/img/table_games/ezugi.png'
        },
        {
          name: 'Evolution',
          thumbnail: '/img/table_games/evolution.png'
        },
        {
          name: 'Blackjack Classic 2',
          thumbnail: '/img/table_games/blackjack.png'
        },
        {
          name: 'Evolution',
          thumbnail: '/img/table_games/evolution1.png'
        },
        {
          name: 'Private Roulette 1',
          thumbnail: '/img/table_games/private_roulette.png'
        },
        {
          name: 'Ezugi',
          thumbnail: '/img/table_games/ezugi.png'
        }
      ]
    }
  }
}
</script>

<style>
.livecasino .v-carousel .v-image__image {
  box-shadow: black 0px 0px 20px 20px inset;
}
.livecasino .v-carousel {
  box-shadow: none;
  border: none;
}
.livecasino .left-menu .v-list__tile {
  height: 74px;
}

.livecasino .mid-menu {
  background-color: #1d1c1c;
  height: 74px;
}

.livecasino .mid-menu .v-btn-toggle .v-btn img {
  width: 100px;
}

.livecasino .mid-menu .v-btn-toggle .v-btn {
  padding-top: 10px;
  padding-bottom: 10px;
  border-radius: 0;
  border-right: none;
  border-left: none;
  transition: padding 0s;
  font-size: 18px;
  padding-left: 15px;
  padding-right: 15px;
  background-color: #1d1c1c;
  cursor: pointer;
}

.livecasino .mid-menu .v-btn-toggle .v-btn--active {
  padding-top: 10px;
  border-bottom: 5px solid green;
  padding-bottom: 5px;
  background-color: #1d1c1c;
}
.livecasino .mid-menu .v-btn-toggle .v-btn {
  opacity: unset;
  min-width: 100px;
}
.livecasino .mid-menu .v-btn-toggle {
  box-shadow: none;
}
.livecasino .mid-menu .v-btn-toggle .v-btn .v-btn__content {
  display: unset;
}
.livecasino .v-list {
  background-color: #1d1c1c;
}
.livecasino .v-list__tile > span {
  width: 25px;
  height: 25px;
  text-align: center;
}
</style>
