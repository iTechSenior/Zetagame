<template>
  <v-app dark>
    <core-header />
    <v-content>
      <div id="core-view" style="background-color: black;">
        <v-fade-transition mode="out-in">
          <v-container style="max-width: 90%;" class="casino">
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
                  Always The
                  <br />
                  <span style="color: #4caf50;">Latest</span> Slots
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
                        <v-list-tile-avatar>
                          <v-icon>mdi-apps</v-icon>
                        </v-list-tile-avatar>
                        <v-list-tile-content class="ml-3"
                          >All Games</v-list-tile-content
                        >
                      </v-list-tile>
                      <v-divider></v-divider>
                      <v-list-tile>
                        <v-list-tile-avatar>
                          <v-icon>mdi-star</v-icon>
                        </v-list-tile-avatar>
                        <v-list-tile-content class="ml-3"
                          >Favorites</v-list-tile-content
                        >
                      </v-list-tile>
                      <v-divider></v-divider>
                      <v-list-tile>
                        <v-list-tile-avatar>
                          <v-icon>mdi-decagram</v-icon>
                        </v-list-tile-avatar>
                        <v-list-tile-content class="ml-3"
                          >New Games</v-list-tile-content
                        >
                      </v-list-tile>
                      <v-divider></v-divider>
                      <v-list-tile>
                        <v-list-tile-avatar>
                          <v-icon>mdi-dice-multiple</v-icon>
                        </v-list-tile-avatar>
                        <v-list-tile-content class="ml-3"
                          >Table Games</v-list-tile-content
                        >
                      </v-list-tile>
                      <v-divider></v-divider>
                      <v-list-tile>
                        <v-list-tile-avatar>
                          <v-icon>mdi-cards-playing-outline</v-icon>
                        </v-list-tile-avatar>
                        <v-list-tile-content class="ml-3"
                          >Video Pockers</v-list-tile-content
                        >
                      </v-list-tile>
                      <v-divider></v-divider>
                      <v-list-tile>
                        <v-list-tile-avatar>
                          <v-icon>mdi-lightbulb-on-outline</v-icon>
                        </v-list-tile-avatar>
                        <v-list-tile-content class="ml-3"
                          >Other Games</v-list-tile-content
                        >
                      </v-list-tile>
                    </v-list>
                  </v-flex>
                  <v-flex xs9>
                    <v-layout class="mid-menu">
                      <v-btn-toggle v-model="toggle_providers" mandatory>
                        <v-btn flat>All</v-btn>
                        <v-btn flat style="text-align: center;">
                          <img src="/img/logos/providers/endorphina.png" />
                        </v-btn>
                        <v-btn flat>
                          <img src="/img/logos/providers/fugaso_logo.png" />
                        </v-btn>
                        <v-btn flat>
                          <img src="/img/logos/providers/quickspin.png" />
                        </v-btn>
                        <v-btn flat>
                          <img
                            src="/img/logos/providers/netent_logo_white.png"
                          />
                        </v-btn>
                      </v-btn-toggle>
                    </v-layout>

                    <v-layout style="display: block; margin-top: 50px;">
                      <v-flex
                        v-for="(game, index) in games"
                        :key="index"
                        style="width: 20%; float: left;"
                        class="pa-1"
                      >
                        <v-card>
                          <v-img
                            :src="game.thumbnail"
                            aspect-ratio="1.5"
                          ></v-img>
                          <v-card-actions class="justify-space-between">
                            {{ game.name }}
                            <v-icon>mdi-star</v-icon>
                          </v-card-actions>
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
          src: '/img/alkemors-tower-free-spins_734x335.png'
        }
      ],
      toggle_providers: 0,
      games: [
        {
          name: "Alkemor's Tower",
          thumbnail: "/img/games/alkemor's_tower.png",
          status: 1
        },
        {
          name: "Alkemor's Tower",
          thumbnail: '/img/games/sin_city_nights.png',
          status: 1
        },
        {
          name: "Alkemor's Tower",
          thumbnail: '/img/games/charms_&_clovers.png',
          status: 1
        },
        {
          name: "Alkemor's Tower",
          thumbnail: '/img/games/slotfather.png',
          status: 1
        },
        {
          name: "Alkemor's Tower",
          thumbnail: "/img/games/pandora's_box.png",
          status: 1
        },
        {
          name: "Alkemor's Tower",
          thumbnail: "/img/games/alkemor's_tower.png",
          status: 1
        },
        {
          name: "Alkemor's Tower",
          thumbnail: '/img/games/sin_city_nights.png',
          status: 1
        },
        {
          name: "Alkemor's Tower",
          thumbnail: '/img/games/charms_&_clovers.png',
          status: 1
        },
        {
          name: "Alkemor's Tower",
          thumbnail: '/img/games/slotfather.png',
          status: 1
        },
        {
          name: "Alkemor's Tower",
          thumbnail: "/img/games/pandora's_box.png",
          status: 1
        },
        {
          name: "Alkemor's Tower",
          thumbnail: "/img/games/alkemor's_tower.png",
          status: 1
        },
        {
          name: "Alkemor's Tower",
          thumbnail: '/img/games/sin_city_nights.png',
          status: 1
        },
        {
          name: "Alkemor's Tower",
          thumbnail: '/img/games/charms_&_clovers.png',
          status: 1
        },
        {
          name: "Alkemor's Tower",
          thumbnail: '/img/games/slotfather.png',
          status: 1
        },
        {
          name: "Alkemor's Tower",
          thumbnail: "/img/games/pandora's_box.png",
          status: 1
        },
        {
          name: "Alkemor's Tower",
          thumbnail: "/img/games/alkemor's_tower.png",
          status: 1
        },
        {
          name: "Alkemor's Tower",
          thumbnail: '/img/games/sin_city_nights.png',
          status: 1
        },
        {
          name: "Alkemor's Tower",
          thumbnail: '/img/games/charms_&_clovers.png',
          status: 1
        },
        {
          name: "Alkemor's Tower",
          thumbnail: '/img/games/slotfather.png',
          status: 1
        },
        {
          name: "Alkemor's Tower",
          thumbnail: "/img/games/pandora's_box.png",
          status: 1
        }
      ]
    }
  }
}
</script>

<style>
.casino .v-carousel .v-image__image {
  box-shadow: black 0px 0px 20px 20px inset;
}
.casino .v-carousel {
  box-shadow: none;
  border: none;
}
.casino .left-menu .v-list__tile {
  height: 74px;
}

.casino .mid-menu {
  background-color: #1d1c1c;
  height: 74px;
}

.casino .mid-menu .v-btn-toggle .v-btn img {
  width: 100px;
}

.casino .mid-menu .v-btn-toggle .v-btn {
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

.casino .mid-menu .v-btn-toggle .v-btn--active {
  padding-top: 10px;
  border-bottom: 5px solid green;
  padding-bottom: 5px;
  background-color: #1d1c1c;
}
.casino .mid-menu .v-btn-toggle .v-btn {
  opacity: unset;
  min-width: 100px;
}
.casino .mid-menu .v-btn-toggle {
  box-shadow: none;
}
.casino .mid-menu .v-btn-toggle .v-btn .v-btn__content {
  display: unset;
}
.casino .v-list {
  background-color: #1d1c1c;
}
</style>
