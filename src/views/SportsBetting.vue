<template>
  <v-app dark>
    <core-header />
    <v-content>
      <div id="core-view">
        <v-fade-transition mode="out-in">
          <v-layout
            class="sports-betting-page"
            style="background: url('/img/bg_sports_betting.png'); background-size: 100% auto"
          >
            <v-flex xs2 class="pl-3 pb-2">
              <v-expansion-panel v-model="panel" expand>
                <v-expansion-panel-content expand-icon="mdi-menu-down">
                  <template v-slot:header>
                    <div>Top Leagues</div>
                  </template>
                  <v-list two-line subheader>
                    <v-list-tile
                      v-for="(item, index) in topLeagues"
                      :key="index"
                    >
                      <img
                        :src="item.icon"
                        style="width: 20px; height: 20px; margin-right: 10px;"
                      />

                      <v-list-tile-content>
                        <v-list-tile-title>
                          {{ item.name }}
                          <span style="float: right;">({{ item.count }})</span>
                        </v-list-tile-title>
                      </v-list-tile-content>
                    </v-list-tile>
                  </v-list>
                </v-expansion-panel-content>
                <v-expansion-panel-content
                  expand-icon="mdi-menu-down"
                  style="background-color: #161616;"
                >
                  <template v-slot:header>
                    <div>Top Leagues</div>
                  </template>
                  <v-card class="pa-2" style="background-color: #161616;">
                    <v-card-text style="border: 1px solid white;">
                      To select favourites, click on star symbols in the betting
                      area
                    </v-card-text>
                  </v-card>
                </v-expansion-panel-content>
                <v-expansion-panel-content
                  expand-icon="mdi-menu-down"
                  style="background-color: #161616;"
                >
                  <template v-slot:header>
                    <div>Time Filters</div>
                  </template>
                  <v-layout row class="pb-2">
                    <v-flex class="text-xs-center">
                      All
                      <br />
                      <div
                        style="border-radius: 50%; background-color: green; width: 10px; height: 10px; margin: auto;"
                      >
                        &nbsp;
                      </div>
                    </v-flex>
                    <v-flex class="text-xs-center">
                      6h
                      <br />
                    </v-flex>
                    <v-flex class="text-xs-center">
                      12h
                      <br />
                    </v-flex>
                    <v-flex class="text-xs-center">
                      24h
                      <br />
                    </v-flex>
                    <v-flex class="text-xs-center">
                      48h
                      <br />
                    </v-flex>
                  </v-layout>
                </v-expansion-panel-content>
              </v-expansion-panel>
              <v-card
                color="#161616"
                style="border-top: 1px solid #303030; height: 70px;"
                class="pa-2"
              >
                <v-text-field
                  append-icon="mdi-magnify"
                  class="mt-2"
                  label="Search"
                  solo-inverted
                ></v-text-field>
              </v-card>
              <v-card color="#161616" style="border-top: 1px solid #303030;">
                <v-card-title class="pb-1">Sports Betting</v-card-title>
                <core-sports-betting-tree-list :items="treeItems" />
              </v-card>
            </v-flex>

            <v-flex xs8 class="pr-3 pb-2 pl-3 mid-panel">
              <v-carousel height="150" hide-delimiters>
                <v-carousel-item
                  v-for="(item, i) in carousel"
                  :key="i"
                  :src="item.src"
                ></v-carousel-item>
              </v-carousel>
              <v-container class="pt-2 pb-0">
                <img src="/img/sports_name_band.png" width="100%" />
              </v-container>
              <v-container class="pt-0 pl-5 pr-5">
                <v-card
                  style="border-bottom: 1px solid hsla(0,0%,100%,.12); box-shadow: none;"
                  height="50"
                  class="pa-2 pl-3 pt-1"
                >
                  <v-card-title primary-title class="pa-0 pt-1">
                    <div
                      style="width: 10px; height: 10px; background-color: green; float:left;"
                    ></div>
                    &nbsp;&nbsp;&nbsp; Live
                    <span style="margin-left: 40px;">Upcoming</span>
                  </v-card-title>
                </v-card>
                <v-card
                  style="border-bottom: 1px solid hsla(0,0%,100%,.12); box-shadow: none;"
                  height="50"
                  class="pa-0"
                >
                  <v-card-title primary-title class="pa-0 pt-1">
                    <v-chip>
                      <img src="/img/football.png" /> &nbsp;Football
                    </v-chip>
                    <v-chip>
                      <img src="/img/basketball.png" /> &nbsp;basketball
                    </v-chip>
                    <v-chip>
                      <img src="/img/volleyball.png" /> &nbsp;Voleyball
                    </v-chip>
                    <v-chip> <img src="/img/tenis.png" /> &nbsp;Tenis </v-chip>
                    <v-flex xs3 class="pt-1 ml-3">
                      <v-autocomplete
                        placeholder="others"
                        class="ma-0 pa-0"
                        height="30px"
                        style="width: 200px;"
                      ></v-autocomplete>
                    </v-flex>
                  </v-card-title>
                </v-card>
                <v-data-table
                  v-for="(table, index) in tables"
                  :id="`table_${index}`"
                  :key="index"
                  :headers="table.headers"
                  :items="table.dataList"
                  class="elevation-1"
                  :pagination.sync="pagination"
                  hide-actions
                >
                  <template slot="headers" slot-scope="props">
                    <tr>
                      <th
                        width="2%"
                        class="icon-expand"
                        @click="toggleTable(`table_${index}`)"
                      >
                        <v-icon>mdi-menu-down</v-icon>
                      </th>
                      <th
                        v-for="(header, id) in props.headers"
                        :key="id"
                        :class="`text-xs-${header.align} ${header.padding}`"
                        :width="header.width"
                      >
                        <flag v-if="header.country" :iso="header.country" />
                        <span v-else>{{ header.text }}</span>
                      </th>
                      <th width="5%"></th>
                    </tr>
                  </template>
                  <template v-slot:items="props">
                    <td></td>
                    <td class="text-xs-center">{{ props.item.score }}</td>
                    <td class="text-xs-left">{{ props.item.gameName }}</td>
                    <td class="text-xs-center">{{ props.item.time }}</td>
                    <td class="text-xs-right">{{ props.item.side1 }}</td>
                    <td class="text-xs-right">{{ props.item.mid }}</td>
                    <td class="text-xs-right">{{ props.item.side2 }}</td>
                    <td class="text-xs-right">{{ props.item.under }}</td>
                    <td></td>
                    <td class="text-xs-right">{{ props.item.over }}</td>
                    <td class="text-xs-center">{{ props.item.plus }}</td>
                    <td class="text-xs-center">
                      <v-icon>mdi-chart-bar-stacked</v-icon>
                    </td>
                  </template>
                </v-data-table>
                <v-card
                  style="border-bottom: 1px solid hsla(0,0%,100%,.12); border-top: 1px solid hsla(0,0%,100%,.12); box-shadow: none;"
                  height="50"
                  class="pa-2 pl-3"
                >
                  <v-card-title primary-title class="pa-0 pt-1">
                    <span style="margin-left: 40px;">Upcoming</span>
                  </v-card-title>
                </v-card>
                <v-data-table
                  id="upcomingTable"
                  :headers="upcomingTable.headers"
                  :items="upcomingTable.dataList"
                  class="elevation-1"
                  :pagination.sync="pagination"
                  hide-actions
                >
                  <template slot="headers" slot-scope="props">
                    <tr>
                      <th
                        width="2%"
                        class="icon-expand"
                        @click="toggleTable('upcomingTable')"
                      >
                        <v-icon>mdi-menu-down</v-icon>
                      </th>
                      <th
                        v-for="(header, id) in props.headers"
                        :key="id"
                        :class="`text-xs-${header.align} ${header.padding}`"
                        :width="header.width"
                      >
                        <flag v-if="header.country" :iso="header.country" />
                        <span v-else>{{ header.text }}</span>
                      </th>
                      <th width="8%"></th>
                    </tr>
                  </template>
                  <template v-slot:items="props">
                    <td></td>
                    <td class="text-xs-center">{{ props.item.dateTime }}</td>
                    <td class="text-xs-left">{{ props.item.gameName }}</td>
                    <td class="text-xs-center">{{ props.item.mbs }}</td>
                    <td class="text-xs-right">{{ props.item.side1 }}</td>
                    <td class="text-xs-right">{{ props.item.mid }}</td>
                    <td class="text-xs-right">{{ props.item.side2 }}</td>
                    <td class="text-xs-right">{{ props.item.under }}</td>
                    <td></td>
                    <td class="text-xs-right">{{ props.item.over }}</td>
                    <td class="text-xs-center">{{ props.item.plus }}</td>
                    <td class="text-xs-center">
                      <v-icon>mdi-chart-bar-stacked</v-icon>
                    </td>
                  </template>
                </v-data-table>
              </v-container>
            </v-flex>

            <v-flex xs2 class="pr-3 pb-2">
              <v-card
                style="background-image: url('/img/bg_bet_slip.png'); background-size: 100% 100%; background-color: transparent; border:none;"
              >
                <v-form
                  id="form_bet_slip"
                  ref="form"
                  v-model="valid"
                  lazy-validation
                >
                  <v-container>
                    <v-layout
                      row
                      justify-space-between
                      class="ma-0 mb-3"
                      height="auto"
                    >
                      <v-flex xs6 class="pa-0 pr-2">
                        <v-btn
                          style="width: 100%; height: 35px;"
                          class="ma-0 pa-0"
                          >Bet Slip</v-btn
                        >
                      </v-flex>
                      <v-flex xs6 class="pa-0 pl-2">
                        <v-btn
                          style="width: 100%; height: 35px;"
                          class="ma-0 pa-0"
                          >Cashout</v-btn
                        >
                      </v-flex>
                    </v-layout>
                    <v-layout row justify-center class="ma-0">
                      <v-btn-toggle
                        v-model="toggle_slip_type"
                        style="width:100%;"
                      >
                        <v-btn flat style="width:33.33%;">Single</v-btn>
                        <v-btn flat style="width:33.33%;">Multiple</v-btn>
                        <v-btn flat style="width:33.33%;">System</v-btn>
                      </v-btn-toggle>
                    </v-layout>
                    <v-container class="pa-0 pt-3">
                      <v-card
                        v-for="(item, index) in slipList"
                        :key="index"
                        class="pa-1 mb-2"
                        color="#161616"
                      >
                        {{ item.name }}
                        <v-btn
                          style="float: right; min-width: 0; position: absolute; top: 10px; right: 5px;"
                          class="pa-0 ma-0"
                          color="#303030"
                        >
                          <v-icon>mdi-close</v-icon>
                        </v-btn>
                        <br />Match Betting
                        <br />
                        Guess:{{ item.guess }}
                        <span style="float: right;">{{ item.rate }}</span>
                      </v-card>
                    </v-container>
                    <v-container class="pa-0 mt-3">
                      <v-card class="pa-1 mb-1" color="#161616">
                        Total Odds:
                        <span style="float: right;">{{ totalOdds }}</span>
                      </v-card>
                      <v-card class="pa-1 mb-1" color="#161616">
                        Quantity:
                        <span style="float: right;">{{ quantity }}</span>
                      </v-card>
                      <v-card class="pa-1 mb-1" color="#161616">
                        Note:
                        <span style="float: right;">{{ note }}</span>
                      </v-card>
                      <v-card class="pa-1 mb-1" color="#161616">
                        Single Match:
                        <span style="float: right;">{{ singleMatch }}</span>
                      </v-card>
                      <v-card class="pa-1 mb-1" color="#161616">
                        Possible Gain:
                        <span style="float: right;">{{ possibleGain }}</span>
                      </v-card>
                      <v-card class="pa-1 mb-1" color="#161616">
                        <v-checkbox
                          v-model="acceptChangingRates"
                          label="Accept Changing Rates!"
                        ></v-checkbox>
                      </v-card>
                    </v-container>
                    <v-layout row justify-space-between class="ma-0 mt-3">
                      <v-flex xs6 class="pa-0 pr-3">
                        <v-btn
                          style="width: 100%; border: 1px solid red; height: 30px;"
                          class="pa-0"
                          >Reset</v-btn
                        >
                      </v-flex>
                      <v-flex xs6 class="pa-0 pl-3">
                        <v-btn
                          style="width: 100%; height: 30px;"
                          class="pa-0"
                          color="green"
                          >Save Slip</v-btn
                        >
                      </v-flex>
                    </v-layout>
                  </v-container>
                </v-form>
              </v-card>
            </v-flex>
          </v-layout>
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
      topLeagues: [
        {
          icon: '/img/uefa.png',
          name: 'UEFA Chanpions League',
          count: '8'
        },
        {
          icon: '/img/uefa.png',
          name: 'UEFA Europe League',
          count: '18'
        },
        {
          icon: '/img/laliga.png',
          name: 'La Liga',
          count: '18'
        },
        {
          icon: '/img/premier.png',
          name: 'Premier League',
          count: '18'
        },
        {
          icon: '/img/bundesliga.png',
          name: 'Bundesliga',
          count: '18'
        },
        {
          icon: '/img/nba.png',
          name: 'NBA',
          count: '18'
        }
      ],
      panel: [true, true, true],
      carousel: [
        {
          src: 'https://cdn.vuetifyjs.com/images/carousel/squirrel.jpg'
        },
        {
          src: 'https://cdn.vuetifyjs.com/images/carousel/sky.jpg'
        },
        {
          src: 'https://cdn.vuetifyjs.com/images/carousel/bird.jpg'
        },
        {
          src: 'https://cdn.vuetifyjs.com/images/carousel/planet.jpg'
        }
      ],
      treeItems: [
        {
          id: 1,
          name: 'Football',
          icon: '/img/football.png',
          count: 689,
          status: 1,
          children: [
            {
              id: 2,
              name: 'England',
              icon: '/img/football.png',
              count: 689,
              status: 1
            },
            {
              id: 3,
              name: 'England Amateur',
              icon: '/img/football.png',
              count: 689,
              status: 1
            },
            {
              id: 4,
              name: 'Germany',
              icon: '/img/football.png',
              count: 689,
              status: 1,
              children: [
                {
                  id: 5,
                  name: 'Bundesliga',
                  icon: '/img/football.png',
                  count: 18,
                  status: 1
                },
                {
                  id: 6,
                  name: 'Bundesliga',
                  icon: '/img/football.png',
                  count: 18,
                  status: 1
                }
              ]
            }
          ]
        },
        {
          id: 7,
          name: 'Basketball',
          icon: '/img/basketball.png',
          count: 689,
          status: 0
        },
        {
          id: 8,
          name: 'Voleyball',
          icon: '/img/basketball.png',
          count: 689,
          status: 0
        },
        {
          id: 9,
          name: 'Tenis',
          icon: '/img/basketball.png',
          count: 689,
          status: 0
        }
      ],
      toggle_slip_type: 0,
      slipList: [
        {
          name: 'SC Fortuna koln - VfR Aalen',
          guess: 1,
          rate: 2.14
        },
        {
          name: 'SC Fortuna koln - VfR Aalen',
          guess: 1,
          rate: 2.14
        },
        {
          name: 'SC Fortuna koln - VfR Aalen',
          guess: 1,
          rate: 2.14
        }
      ],
      totalOdds: 21.85,
      quantity: 21.85,
      note: 'abc',
      singleMatch: 21.85,
      possibleGain: 21.85,
      acceptChangingRates: true,

      tables: [
        {
          headers: [
            { country: 'br', value: 'score', width: '10%', aligh: 'right' },
            {
              text: 'Brezilya - International  Lig',
              value: 'gameName',
              align: 'left',
              width: '40%'
            },
            { text: '', value: 'time', align: 'left', width: '8%' },
            {
              text: '1',
              value: 'side1',
              align: 'right',
              padding: 'pr-2',
              width: '5%'
            },
            {
              text: 'X',
              value: 'mid',
              align: 'right',
              padding: 'pr-2',
              width: '5%'
            },
            {
              text: '2',
              value: 'side2',
              align: 'right',
              padding: 'pr-2',
              width: '5%'
            },
            {
              text: 'Under',
              value: 'under',
              align: 'right',
              padding: 'pr-2',
              width: '5%'
            },
            { text: '2.5', value: null, align: 'right', width: '5%' },
            {
              text: 'Over',
              value: 'under',
              align: 'right',
              padding: 'pr-2',
              width: '5%'
            },
            { text: '+', value: 'plus', align: 'center', width: '5%' }
          ],
          dataList: [
            {
              score: '0-2',
              gameName: 'Hertha BSC Berlin  -  Holstein Kiel',
              time: "2H 01'",
              side1: 3.24,
              mid: 1.63,
              side2: 1.24,
              under: 3.24,
              over: 1.24,
              plus: 235
            },
            {
              score: '0-2',
              gameName: 'FC Yenisey Krasnoyarsk - FK Rostov',
              time: "1H 23'",
              side1: 3.24,
              mid: 1.63,
              side2: 1.24,
              under: 3.24,
              over: 1.24,
              plus: 235
            },
            {
              score: '0-2',
              gameName: 'SC Paderborn 07 - 1. FC Köln',
              time: "1H 13'",
              side1: 3.24,
              mid: 1.63,
              side2: 1.24,
              under: 3.24,
              over: 1.24,
              plus: 235
            }
          ]
        },
        {
          headers: [
            { country: 'gb', value: 'score', width: '10%', aligh: 'right' },
            {
              text: 'İngiltere / Premier League, Championship Round',
              value: 'gameName',
              align: 'left',
              width: '40%'
            },
            { text: '', value: 'time', align: 'left', width: '8%' },
            {
              text: '1',
              value: 'side1',
              align: 'right',
              padding: 'pr-2',
              width: '5%'
            },
            {
              text: 'X',
              value: 'mid',
              align: 'right',
              padding: 'pr-2',
              width: '5%'
            },
            {
              text: '2',
              value: 'side2',
              align: 'right',
              padding: 'pr-2',
              width: '5%'
            },
            {
              text: 'Under',
              value: 'under',
              align: 'right',
              padding: 'pr-2',
              width: '5%'
            },
            { text: '2.5', value: null, align: 'right', width: '5%' },
            {
              text: 'Over',
              value: 'under',
              align: 'right',
              padding: 'pr-2',
              width: '5%'
            },
            { text: '+', value: 'plus', align: 'center', width: '5%' }
          ],
          dataList: [
            {
              score: '0-2',
              gameName: 'Hertha BSC Berlin  -  Holstein Kiel',
              time: "2H 01'",
              side1: 3.24,
              mid: 1.63,
              side2: 1.24,
              under: 3.24,
              over: 1.24,
              plus: 235
            },
            {
              score: '0-2',
              gameName: 'FC Yenisey Krasnoyarsk - FK Rostov',
              time: "1H 23'",
              side1: 3.24,
              mid: 1.63,
              side2: 1.24,
              under: 3.24,
              over: 1.24,
              plus: 235
            },
            {
              score: '0-2',
              gameName: 'SC Paderborn 07 - 1. FC Köln',
              time: "1H 13'",
              side1: 3.24,
              mid: 1.63,
              side2: 1.24,
              under: 3.24,
              over: 1.24,
              plus: 235
            }
          ]
        }
      ],
      upcomingTable: {
        headers: [
          { country: 'de', value: 'dateTime', width: '10%' },
          {
            text: 'Almanya Amatör / Oberliga NOFV South',
            value: 'gameName',
            align: 'left',
            width: '40%'
          },
          { text: 'MBS', value: 'mbs', align: 'center', width: '8%' },
          {
            text: '1',
            value: 'side1',
            align: 'right',
            padding: 'pr-2',
            width: '5%'
          },
          {
            text: 'X',
            value: 'mid',
            align: 'right',
            padding: 'pr-2',
            width: '5%'
          },
          {
            text: '2',
            value: 'side2',
            align: 'right',
            padding: 'pr-2',
            width: '5%'
          },
          {
            text: 'Alt',
            value: 'under',
            align: 'right',
            padding: 'pr-2',
            width: '5%'
          },
          { text: '2.5', value: null, align: 'right', width: '5%' },
          {
            text: 'Üst',
            value: 'over',
            align: 'right',
            padding: 'pr-2',
            width: '5%'
          },
          { text: '+', value: 'plus', align: 'center', width: '5%' }
        ],
        dataList: [
          {
            dateTime: '25/03 22.30',
            gameName: 'Hertha BSC Berlin  -  Holstein Kiel',
            mbs: 3,
            side1: 3.24,
            mid: 1.63,
            side2: 1.24,
            under: 3.24,
            over: 1.24,
            plus: 235
          },
          {
            dateTime: '25/03 22.30',
            gameName: 'FC Yenisey Krasnoyarsk - FK Rostov',
            mbs: 3,
            side1: 3.24,
            mid: 1.63,
            side2: 1.24,
            under: 3.24,
            over: 1.24,
            plus: 235
          },
          {
            dateTime: '25/03 22.30',
            gameName: 'SC Paderborn 07 - 1. FC Köln',
            mbs: 3,
            side1: 3.24,
            mid: 1.63,
            side2: 1.24,
            under: 3.24,
            over: 1.24,
            plus: 235
          },
          {
            dateTime: '25/03 22.30',
            gameName: 'SC Paderborn 07 - 1. FC Köln',
            mbs: 3,
            side1: 3.24,
            mid: 1.63,
            side2: 1.24,
            under: 3.24,
            over: 1.24,
            plus: 235
          },
          {
            dateTime: '25/03 22.30',
            gameName: 'SC Paderborn 07 - 1. FC Köln',
            mbs: 3,
            side1: 3.24,
            mid: 1.63,
            side2: 1.24,
            under: 3.24,
            over: 1.24,
            plus: 235
          },
          {
            dateTime: '25/03 22.30',
            gameName: 'SC Paderborn 07 - 1. FC Köln',
            mbs: 3,
            side1: 3.24,
            mid: 1.63,
            side2: 1.24,
            under: 3.24,
            over: 1.24,
            plus: 235
          },
          {
            dateTime: '25/03 22.30',
            gameName: 'SC Paderborn 07 - 1. FC Köln',
            mbs: 3,
            side1: 3.24,
            mid: 1.63,
            side2: 1.24,
            under: 3.24,
            over: 1.24,
            plus: 235
          },
          {
            dateTime: '25/03 22.30',
            gameName: 'SC Paderborn 07 - 1. FC Köln',
            mbs: 3,
            side1: 3.24,
            mid: 1.63,
            side2: 1.24,
            under: 3.24,
            over: 1.24,
            plus: 235
          },
          {
            dateTime: '25/03 22.30',
            gameName: 'SC Paderborn 07 - 1. FC Köln',
            mbs: 3,
            side1: 3.24,
            mid: 1.63,
            side2: 1.24,
            under: 3.24,
            over: 1.24,
            plus: 235
          },
          {
            dateTime: '25/03 22.30',
            gameName: 'SC Paderborn 07 - 1. FC Köln',
            mbs: 3,
            side1: 3.24,
            mid: 1.63,
            side2: 1.24,
            under: 3.24,
            over: 1.24,
            plus: 235
          },
          {
            dateTime: '25/03 22.30',
            gameName: 'SC Paderborn 07 - 1. FC Köln',
            mbs: 3,
            side1: 3.24,
            mid: 1.63,
            side2: 1.24,
            under: 3.24,
            over: 1.24,
            plus: 235
          },
          {
            dateTime: '25/03 22.30',
            gameName: 'SC Paderborn 07 - 1. FC Köln',
            mbs: 3,
            side1: 3.24,
            mid: 1.63,
            side2: 1.24,
            under: 3.24,
            over: 1.24,
            plus: 235
          },
          {
            dateTime: '25/03 22.30',
            gameName: 'SC Paderborn 07 - 1. FC Köln',
            mbs: 3,
            side1: 3.24,
            mid: 1.63,
            side2: 1.24,
            under: 3.24,
            over: 1.24,
            plus: 235
          },
          {
            dateTime: '25/03 22.30',
            gameName: 'SC Paderborn 07 - 1. FC Köln',
            mbs: 3,
            side1: 3.24,
            mid: 1.63,
            side2: 1.24,
            under: 3.24,
            over: 1.24,
            plus: 235
          },
          {
            dateTime: '25/03 22.30',
            gameName: 'SC Paderborn 07 - 1. FC Köln',
            mbs: 3,
            side1: 3.24,
            mid: 1.63,
            side2: 1.24,
            under: 3.24,
            over: 1.24,
            plus: 235
          },
          {
            dateTime: '25/03 22.30',
            gameName: 'SC Paderborn 07 - 1. FC Köln',
            mbs: 3,
            side1: 3.24,
            mid: 1.63,
            side2: 1.24,
            under: 3.24,
            over: 1.24,
            plus: 235
          },
          {
            dateTime: '25/03 22.30',
            gameName: 'SC Paderborn 07 - 1. FC Köln',
            mbs: 3,
            side1: 3.24,
            mid: 1.63,
            side2: 1.24,
            under: 3.24,
            over: 1.24,
            plus: 235
          },
          {
            dateTime: '25/03 22.30',
            gameName: 'SC Paderborn 07 - 1. FC Köln',
            mbs: 3,
            side1: 3.24,
            mid: 1.63,
            side2: 1.24,
            under: 3.24,
            over: 1.24,
            plus: 235
          },
          {
            dateTime: '25/03 22.30',
            gameName: 'SC Paderborn 07 - 1. FC Köln',
            mbs: 3,
            side1: 3.24,
            mid: 1.63,
            side2: 1.24,
            under: 3.24,
            over: 1.24,
            plus: 235
          }
        ]
      },
      valid: false,
      pagination: {
        rowsPerPage: -1
      }
    }
  },
  methods: {
    toggleTable(tableId) {
      let element = document.querySelector(`#${tableId} tbody`)
      if (!element) return
      let computedStyle = window.getComputedStyle(element)
      let displayValue = computedStyle.getPropertyValue('display')
      if (displayValue === 'none') displayValue = 'table-row-group'
      else displayValue = 'none'
      element.style.display = displayValue
    }
  }
}
</script>

<style>
.sports-betting-page .v-list__tile {
  height: 30px !important;
  cursor: pointer;
}
.sports-betting-page .v-list__tile:hover {
  background-color: #303030;
}

.sports-betting-page
  .v-text-field.v-text-field--enclosed
  .v-input__append-inner {
  margin-top: 1px;
}
.v-text-field--solo input {
  padding: 8px 0px;
}
.v-card {
  border-radius: 0;
}
#form_bet_slip .v-btn-toggle .v-btn {
  padding-top: 10px;
  padding-bottom: 10px;
  border-radius: 0;
  border-right: none;
  border-left: none;
  transition: padding 0s;
  font-size: 14px;
  padding-left: 15px;
  padding-right: 15px;
}
#form_bet_slip .v-btn-toggle .v-btn--active {
  padding-top: 10px;
  border-bottom: 5px solid green;
  padding-bottom: 5px;
}

#form_bet_slip .v-input--checkbox {
  margin-top: 0;
}
#form_bet_slip .v-input--checkbox .v-input__control {
  height: 22px;
}
#form_bet_slip .v-input--checkbox .v-input__slot {
  margin: 0;
}
.mid-panel .v-select .v-input__slot {
  margin: 0;
}
.mid-panel .v-select .v-input__control {
  height: 30px;
}
.v-chip .v-chip__content {
  cursor: pointer;
}
.v-chip img {
  width: 16px;
  height: 16px;
}
.mid-panel table.v-table thead {
  background-image: linear-gradient(#006600, #001a00);
  padding-top: 5px;
  padding-bottom: 5px;
  min-height: 30px;
}
.flag-icon {
  width: 20px !important;
  height: 13px;
  background-size: 100% 100%;
}
.mid-panel table.v-table thead tr {
  height: 40px;
}
.mid-panel table.v-table tbody td {
  padding: 5px 10px;
}
.icon-expand {
  cursor: pointer;
}
</style>
