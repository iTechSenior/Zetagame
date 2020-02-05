<template>
  <v-app dark>
    <core-header />
    <v-content>
      <div id="core-view">
        <v-fade-transition mode="out-in">
          <v-layout
            class="pa-4"
            style="background: url('/img/bg_sports_betting.png'); background-size: 100% auto"
          >
            <v-flex v-if="view == 0" xs10 class="overview">
              <v-container
                style="background-color: #161616; width: 100%; max-width: unset;"
                class="ma-0 pa-0 overview-menu"
              >
                <v-layout style="background-color: black;">
                  <v-btn flat @click="view = 0">
                    <v-icon>mdi-format-list-bulleted</v-icon>&nbsp;Overview
                  </v-btn>
                  <v-btn flat @click="view = 1">
                    <v-icon>mdi-folder-outline</v-icon>&nbsp;Event View
                  </v-btn>
                  <v-btn flat>
                    <v-icon>mdi-calendar</v-icon>&nbsp;Calendar
                  </v-btn>
                </v-layout>
                <v-layout>
                  <v-btn-toggle v-model="toggle_sports" mandatory>
                    <v-btn flat>All</v-btn>
                    <v-btn flat style="text-align: center;">
                      <img src="/img/football.png" width="30" />
                      <br />
                      <span>Soccer (150)</span>
                    </v-btn>
                    <v-btn flat>
                      <img src="/img/basketball.png" width="30" />
                      <br />basketball (150)
                    </v-btn>
                    <v-btn flat>
                      <img src="/img/tenis.png" width="30" />
                      <br />Tenis (150)
                    </v-btn>
                    <v-btn flat>
                      <img src="/img/volleyball.png" width="30" />
                      <br />Volleyball (150)
                    </v-btn>
                    <v-btn flat>
                      <img src="/img/baseball.png" width="30" />
                      <br />Baseball (150)
                    </v-btn>
                  </v-btn-toggle>
                </v-layout>
                <v-layout class="pt-2 pb-2" style="background-color: #303030;">
                  <v-flex style="width: 5%;"></v-flex>
                  <v-flex style="width: 35%;">
                    <img
                      src="/img/soccer.png"
                      alt="soccer"
                      style="position: relative; top: 5px;"
                    />&nbsp; Soccer
                  </v-flex>
                  <v-flex style="width: 5%;"></v-flex>
                  <v-flex style="width: 5%;"></v-flex>
                  <v-flex style="width: 15%;">
                    <v-layout justify-center>3 Way</v-layout>
                    <v-layout>
                      <v-flex xs4 class="text-xs-center">1</v-flex>
                      <v-flex xs4 class="text-xs-center">X</v-flex>
                      <v-flex xs4 class="text-xs-center">2</v-flex>
                    </v-layout>
                  </v-flex>
                  <v-flex style="width: 5%;"></v-flex>
                  <v-flex style="width: 10%;">
                    <v-layout justify-center>Total Goals</v-layout>
                    <v-layout>
                      <v-flex xs6 class="text-xs-center">Over</v-flex>
                      <v-flex xs6 class="text-xs-center">Under</v-flex>
                    </v-layout>
                  </v-flex>
                  <v-flex style="width: 15%;">
                    <v-layout justify-center>Next Goal</v-layout>
                    <v-layout>
                      <v-flex xs4 class="text-xs-center">1</v-flex>
                      <v-flex xs4 class="text-xs-center">X</v-flex>
                      <v-flex xs4 class="text-xs-center">2</v-flex>
                    </v-layout>
                  </v-flex>
                  <v-flex style="width: 5%;"></v-flex>
                </v-layout>
                <v-expansion-panel v-model="expandPanel" expand>
                  <v-expansion-panel-content>
                    <template v-slot:header>
                      <div>
                        <flag
                          iso="bg"
                        />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;England
                        Premium League
                      </div>
                    </template>

                    <v-data-table
                      id="upcomingTable"
                      :headers="upcomingTable.headers"
                      :items="upcomingTable.dataList"
                      class="elevation-1"
                      :pagination.sync="pagination"
                      hide-actions
                      hide-headers
                    >
                      <template v-slot:items="props">
                        <td width="5%" class="text-xs-center">
                          {{ props.item.time }}
                        </td>
                        <td width="35%">
                          <v-icon>mdi-star</v-icon>
                          &nbsp;{{ props.item.gameName }}
                        </td>
                        <td width="5%" class="text-xs-center">
                          <v-icon color="grey">mdi-eye-outline</v-icon>
                        </td>
                        <td width="5%" class="text-xs-left">
                          {{ props.item.score }}
                        </td>
                        <td width="5%" class="text-xs-center">
                          {{ props.item.side1 }}
                        </td>
                        <td width="5%" class="text-xs-center">
                          {{ props.item.mid }}
                        </td>
                        <td width="5%" class="text-xs-center">
                          {{ props.item.side2 }}
                        </td>
                        <td width="5%" class="text-xs-center">1.5</td>
                        <td width="5%" class="text-xs-cetner">
                          {{ props.item.over }}
                        </td>
                        <td width="5%" class="text-xs-center">
                          {{ props.item.under }}
                        </td>
                        <td width="5%" class="text-xs-center">
                          {{ props.item.nextSide1 }}
                        </td>
                        <td class="text-xs-center">{{ props.item.nextMid }}</td>
                        <td class="text-xs-center">
                          {{ props.item.nextSide2 }}
                        </td>
                        <td class="text-xs-center">{{ props.item.header3 }}</td>
                      </template>
                    </v-data-table>
                  </v-expansion-panel-content>
                  <v-expansion-panel-content>
                    <template v-slot:header>
                      <div>
                        <flag
                          iso="bg"
                        />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;England
                        Premium League
                      </div>
                    </template>

                    <v-data-table
                      id="upcomingTable"
                      :headers="upcomingTable.headers"
                      :items="upcomingTable.dataList"
                      class="elevation-1"
                      :pagination.sync="pagination"
                      hide-actions
                      hide-headers
                    >
                      <template v-slot:items="props">
                        <td width="5%" class="text-xs-center">
                          {{ props.item.time }}
                        </td>
                        <td width="35%">
                          <v-icon>mdi-star</v-icon>
                          &nbsp;{{ props.item.gameName }}
                        </td>
                        <td width="5%" class="text-xs-center">
                          <v-icon color="grey">mdi-eye-outline</v-icon>
                        </td>
                        <td width="5%" class="text-xs-left">
                          {{ props.item.score }}
                        </td>
                        <td width="5%" class="text-xs-center">
                          {{ props.item.side1 }}
                        </td>
                        <td width="5%" class="text-xs-center">
                          {{ props.item.mid }}
                        </td>
                        <td width="5%" class="text-xs-center">
                          {{ props.item.side2 }}
                        </td>
                        <td width="5%" class="text-xs-center">1.5</td>
                        <td width="5%" class="text-xs-cetner">
                          {{ props.item.over }}
                        </td>
                        <td width="5%" class="text-xs-center">
                          {{ props.item.under }}
                        </td>
                        <td width="5%" class="text-xs-center">
                          {{ props.item.nextSide1 }}
                        </td>
                        <td class="text-xs-center">{{ props.item.nextMid }}</td>
                        <td class="text-xs-center">
                          {{ props.item.nextSide2 }}
                        </td>
                        <td class="text-xs-center">{{ props.item.header3 }}</td>
                      </template>
                    </v-data-table>
                  </v-expansion-panel-content>
                </v-expansion-panel>
              </v-container>
            </v-flex>
            <v-flex v-if="view == 1" xs2 class="pr-4 eventview">
              <v-expansion-panel v-model="expandPanel" expand>
                <v-expansion-panel-content
                  expand-icon="mdi-menu-down"
                  style="background-color: #161616;"
                >
                  <template v-slot:header>
                    <div>Top Leagues</div>
                  </template>
                  <v-card class="pa-2" style="background-color: #161616;">
                    <v-card-text style="border: 1px solid grey;">
                      To select favourites, click on star symbols in the betting
                      area
                    </v-card-text>
                    <v-text-field
                      append-icon="mdi-magnify"
                      class="mt-2"
                      label="Search"
                      solo-inverted
                      hide-details
                    ></v-text-field>
                  </v-card>
                </v-expansion-panel-content>
                <v-expansion-panel-content
                  expand-icon="mdi-menu-down"
                  style="background-color: #282828;"
                >
                  <template v-slot:header>
                    <div style="align-items: center; display: flex;">
                      <img src="/img/football.png" />&nbsp; Football (21)
                    </div>
                  </template>
                  <v-list style="background-color: #161616;">
                    <v-list-tile ripple style="background-color: #282828;">
                      <v-list-tile-avatar>
                        <flag iso="it" />
                      </v-list-tile-avatar>
                      <v-list-tile-content>
                        <v-list-tile-title>
                          Turkey Amateur - 2. Lig Beyaz Grup Güney
                        </v-list-tile-title>
                      </v-list-tile-content>
                    </v-list-tile>
                    <v-divider></v-divider>
                    <v-list-tile ripple style="background-color: #303030;">
                      <v-list-tile-avatar>
                        <v-icon>mdi-star</v-icon>
                      </v-list-tile-avatar>
                      <v-list-tile-content>
                        <v-list-tile-title>
                          <v-layout>
                            <v-flex xs8>
                              team1
                              <br />team2
                            </v-flex>
                            <v-flex xs4 class="text-xs-center">
                              <span class="score">-:-</span>
                              <br />Not Started
                            </v-flex>
                          </v-layout>
                        </v-list-tile-title>
                      </v-list-tile-content>
                    </v-list-tile>
                    <v-divider></v-divider>
                    <v-list-tile
                      ripple
                      style="background-color: #303030; border-bottom: 1px solid #383838;"
                    >
                      <v-list-tile-avatar>
                        <v-icon>mdi-star</v-icon>
                      </v-list-tile-avatar>
                      <v-list-tile-content>
                        <v-list-tile-title>
                          <v-layout>
                            <v-flex xs8>
                              team1
                              <br />team2
                            </v-flex>
                            <v-flex xs4 class="text-xs-center">
                              <span class="score">2:1</span>
                              <br />1st Half 33'
                            </v-flex>
                          </v-layout>
                        </v-list-tile-title>
                      </v-list-tile-content>
                    </v-list-tile>
                    <v-divider></v-divider>
                  </v-list>
                </v-expansion-panel-content>
                <v-expansion-panel-content
                  expand-icon="mdi-menu-down"
                  style="background-color: #282828;"
                >
                  <template v-slot:header>
                    <div style="align-items: center; display: flex;">
                      <img src="/img/basketball.png" />&nbsp; Basketball (39)
                    </div>
                  </template>
                </v-expansion-panel-content>
              </v-expansion-panel>
            </v-flex>
            <v-flex v-if="view == 1" xs8 class="eventview">
              <v-container
                class="pa-0 ma-0"
                style="background-color: black; max-width: 100%;"
              >
                <v-layout style="background-color: black;">
                  <v-btn flat @click="view = 0">
                    <v-icon>mdi-format-list-bulleted</v-icon>&nbsp;Overview
                  </v-btn>
                  <v-btn flat @click="view = 1">
                    <v-icon>mdi-folder-outline</v-icon>&nbsp;Event View
                  </v-btn>
                  <v-btn flat>
                    <v-icon>mdi-calendar</v-icon>&nbsp;Calendar
                  </v-btn>
                </v-layout>
                <v-layout>
                  <v-flex
                    style="display: flex; align-items: center;"
                    class="ml-4"
                  >
                    <v-icon>mdi-less-than</v-icon>Geri Git
                    <v-breadcrumbs
                      :items="breadcrumbs"
                      divider=">"
                    ></v-breadcrumbs>
                  </v-flex>
                </v-layout>
                <v-layout
                  style="background-image: url('/img/livebetbanner.png'); background-size: 100% auto; background-position: 0,-200px; height:200px; display: block;"
                >
                  <v-flex
                    style="background-color: black; opacity: .4; height: 100%; position: relative; top: 0px; left: 0px;"
                  ></v-flex>
                  <v-flex
                    style="position: relative; top: -200px; left: 0px; font-size: 16px;"
                  >
                    <v-layout class="pa-3 pt-5">
                      <v-flex xs1></v-flex>
                      <v-flex>International Clubs - Club Friendly Games</v-flex>
                    </v-layout>
                    <v-layout class="pa-2">
                      <v-flex xs6 class="text-xs-right"
                        >Lokomotiv Moscow &nbsp;0&nbsp;</v-flex
                      >:
                      <v-flex xs6>&nbsp;0&nbsp; FC UFA</v-flex>
                    </v-layout>
                    <v-layout class="pa-3">
                      <v-flex xs6 class="text-xs-right">
                        <img src="/img/icon1.png" />
                      </v-flex>
                      <v-flex xs2 class="text-xs-center">1st Half 43'</v-flex>
                      <v-flex xs6>
                        <img src="/img/icon1.png" />
                      </v-flex>
                    </v-layout>
                  </v-flex>
                </v-layout>

                <v-layout>
                  <v-btn-toggle
                    v-model="toggle_kinds"
                    mandatory
                    style="width: 100%; display: block"
                  >
                    <v-btn flat style="width: 12.5%">All</v-btn>
                    <v-btn flat style="width: 12.5%">Results</v-btn>
                    <v-btn flat style="width: 12.5%">1st Half</v-btn>
                    <v-btn flat style="width: 12.5%">2nd Half</v-btn>
                    <v-btn flat style="width: 12.5%">Total</v-btn>
                    <v-btn flat style="width: 12.5%">Handicap</v-btn>
                    <v-btn flat style="width: 12.5%">Correct Score</v-btn>
                    <v-btn flat style="width: 12.5%">Corners</v-btn>
                    <v-btn flat style="width: 12.5%">Fouls</v-btn>
                    <v-btn flat style="width: 12.5%">Shots On Target</v-btn>
                    <v-btn flat style="width: 12.5%">Offsides</v-btn>
                    <v-btn flat style="width: 12.5%">Spec.Bets</v-btn>
                    <v-btn flat style="width: 12.5%">Minutes</v-btn>
                    <v-btn flat style="width: 12.5%">Cards</v-btn>
                  </v-btn-toggle>
                </v-layout>
                <v-layout style="font-size: 16px;" class="mid-panel">
                  <v-flex
                    xs6
                    class="pa-1 mr-1"
                    style="background-color: #161616;"
                  >
                    <h4 class="pl-3 mb-1">Which Team Has Kick Off?</h4>
                    <v-layout>
                      <v-flex xs6 class="pa-1 mr-1 label">
                        1
                        <span style="float: right; color: red;">1.90</span>
                      </v-flex>
                      <v-flex xs6 class="pa-1 label">
                        1
                        <span style="float: right;">1.90</span>
                      </v-flex>
                    </v-layout>
                    <h4 class="pl-3 mb-1">Match Result</h4>
                    <v-layout>
                      <v-flex xs4 class="pa-1 mr-1 label">
                        1
                        <span style="float: right; color: lawngreen;"
                          >12.90</span
                        >
                      </v-flex>
                      <v-flex xs4 class="pa-1 mr-1 label">
                        X
                        <span style="float: right;">12.90</span>
                      </v-flex>
                      <v-flex xs4 class="pa-1 label">
                        2
                        <span style="float: right;">12.90</span>
                      </v-flex>
                    </v-layout>
                    <h4 class="pl-3 mb-1">Matchflow</h4>
                    <v-layout>
                      <ul style="width: 100%;" class="pl-0">
                        <li>
                          Hometeam Scores First And Home
                          <span style="float: right;">12.90</span>
                        </li>
                        <li>
                          Hometeam Scores First And Draw
                          <span style="float: right;">12.90</span>
                        </li>
                        <li>
                          Hometeam Scores First And Away
                          <span style="float: right;">12.90</span>
                        </li>
                        <li>
                          Awayteam Scores First And Home
                          <span style="float: right;">12.90</span>
                        </li>
                        <li>
                          Awayteam Scores First And Draw
                          <span style="float: right;">12.90</span>
                        </li>
                        <li>
                          Awayteam Scores First And Away
                          <span style="float: right;">12.90</span>
                        </li>
                        <li>
                          No Goal
                          <span style="float: right;">12.90</span>
                        </li>
                      </ul>
                    </v-layout>
                  </v-flex>
                  <v-flex xs6 class="pa-1" style="background-color: #161616;">
                    <h4 class="pl-3 mb-1">Which Team Has Kick Off?</h4>
                    <v-layout>
                      <v-flex xs6 class="pa-1 mr-1 label">
                        1
                        <span style="float: right; color: red;">1.90</span>
                      </v-flex>
                      <v-flex xs6 class="pa-1 label">
                        1
                        <span style="float: right;">1.90</span>
                      </v-flex>
                    </v-layout>
                    <h4 class="pl-3 mb-1">Match Result</h4>
                    <v-layout>
                      <v-flex xs4 class="pa-1 mr-1 label">
                        1
                        <span style="float: right; color: red;">12.90</span>
                      </v-flex>
                      <v-flex xs4 class="pa-1 mr-1 label">
                        X
                        <span style="float: right;">12.90</span>
                      </v-flex>
                      <v-flex xs4 class="pa-1 label">
                        2
                        <span style="float: right;">12.90</span>
                      </v-flex>
                    </v-layout>
                    <h4 class="pl-3 mb-1">Matchflow</h4>
                    <v-layout>
                      <ul style="width: 100%;" class="pl-0">
                        <li>
                          Hometeam Scores First And Home
                          <span style="float: right;">12.90</span>
                        </li>
                        <li>
                          Hometeam Scores First And Draw
                          <span style="float: right;">12.90</span>
                        </li>
                        <li>
                          Hometeam Scores First And Away
                          <span style="float: right;">12.90</span>
                        </li>
                        <li>
                          Awayteam Scores First And Home
                          <span style="float: right;">12.90</span>
                        </li>
                        <li>
                          Awayteam Scores First And Draw
                          <span style="float: right;">12.90</span>
                        </li>
                        <li>
                          Awayteam Scores First And Away
                          <span style="float: right;">12.90</span>
                        </li>
                        <li>
                          No Goal
                          <span style="float: right;">12.90</span>
                        </li>
                      </ul>
                    </v-layout>
                  </v-flex>
                </v-layout>
              </v-container>
            </v-flex>
            <v-flex xs2 class="pl-4">
              <div
                class="text-xs-center pa-1"
                style="background-color: #161616;"
              >
                China 0:0 Uzbekistan
              </div>
              <v-img src="/img/football_game.png"></v-img>
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

<script lang="ts">
export default {
  data() {
    return {
      toggle_sports: 0,
      upcomingTable: {
        headers: [
          {
            text: 'Time',
            value: 'time'
          },
          { text: 'Game Name', value: 'gameName' },
          { text: 'Header1', value: 'header1' },
          {
            text: 'Score',
            value: 'score'
          },
          {
            text: '1',
            value: 'side1'
          },
          {
            text: 'X',
            value: 'mid'
          },
          { text: '2', value: 'side2' },
          {
            text: 'Header2',
            value: 'header2'
          },
          { text: 'Over', value: 'over' },
          { text: 'Under', value: 'under' },
          { text: '1', value: 'nextSide1' },
          { text: 'X', value: 'nextMid' },
          { text: '2', value: 'nextSide2' },
          { text: 'Header3', value: 'header3' }
        ],
        dataList: [
          {
            time: "90'",
            gameName: 'Hertha BSC Berlin  -  Holstein Kiel',
            header1: null,
            score: '1:2',
            side1: 3.24,
            mid: 1.63,
            side2: 1.24,
            header2: null,
            over: 1.24,
            under: 3.24,
            nextSide1: 3.24,
            nextMid: 1.63,
            nextSide2: 1.24,
            header3: '+105'
          },
          {
            time: "90'",
            gameName: 'Hertha BSC Berlin  -  Holstein Kiel',
            header1: null,
            score: '1:2',
            side1: 3.24,
            mid: 1.63,
            side2: 1.24,
            header2: null,
            over: 1.24,
            under: 3.24,
            nextSide1: 3.24,
            nextMid: 1.63,
            nextSide2: 1.24,
            header3: '+105'
          },
          {
            time: "90'",
            gameName: 'Hertha BSC Berlin  -  Holstein Kiel',
            header1: null,
            score: '1:2',
            side1: 3.24,
            mid: 1.63,
            side2: 1.24,
            header2: null,
            over: 1.24,
            under: 3.24,
            nextSide1: 3.24,
            nextMid: 1.63,
            nextSide2: 1.24,
            header3: '+105'
          }
        ]
      },
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
      valid: false,
      pagination: {
        rowsPerPage: -1
      },
      toggle_slip_type: 0,
      toggle_kinds: 0,
      expandPanel: [
        true,
        true,
        true,
        true,
        true,
        true,
        true,
        true,
        true,
        true,
        true,
        true
      ],
      view: 0,
      breadcrumbs: [
        {
          text: 'Dashboard',
          disabled: false,
          href: 'breadcrumbs_dashboard'
        },
        {
          text: 'Link 1',
          disabled: false,
          href: 'breadcrumbs_link_1'
        },
        {
          text: 'Link 2',
          disabled: true,
          href: 'breadcrumbs_link_2'
        }
      ]
    }
  }
}
</script>

<style>
.overview-menu .v-btn-toggle .v-btn,
.eventview .v-btn-toggle .v-btn {
  padding-top: 10px;
  padding-bottom: 10px;
  border-radius: 0;
  border-right: none;
  border-left: none;
  transition: padding 0s;
  font-size: 14px;
  padding-left: 15px;
  padding-right: 15px;
  background-color: #161616;
}
.eventview .v-btn-toggle .v-btn {
  height: 50px;
  background-color: #424242;
}
.overview-menu .v-btn-toggle .v-btn--active,
.eventview .v-btn-toggle .v-btn--active {
  padding-top: 10px;
  border-bottom: 5px solid green;
  padding-bottom: 5px;
  background-color: #161616;
}
.overview-menu .v-btn-toggle .v-btn,
.eventview .v-btn-toggle .v-btn {
  opacity: unset;
  min-width: 100px;
}
.overview-menu .v-btn-toggle,
.eventview .v-btn-toggle {
  box-shadow: none;
}
.overview-menu .v-btn-toggle .v-btn .v-btn__content,
.eventview .v-btn-toggle .v-btn .v-btn__content {
  display: unset;
}

.overview .v-expansion-panel__header {
  background-image: linear-gradient(#006600, #001a00);
  padding-top: 5px;
  padding-bottom: 5px;
  min-height: 30px;
}
.overview table.v-table tbody {
  background-color: #161616;
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
  padding-top: 0;
}
#form_bet_slip .v-input--checkbox .v-input__control {
  height: 22px;
}
#form_bet_slip .v-input--checkbox .v-input__slot {
  margin: 0;
}
.eventview .v-list {
  padding: 5px 0;
}
.eventview .v-list__tile__title {
  font-size: 12px;
  height: auto;
}
.score {
  color: lawngreen;
  font-size: 16px;
}
.theme--dark.v-divider {
  border-color: hsla(0, 0%, 100%, 0.2);
}
.mid-panel .label {
  background-color: #303030;
}
.mid-panel li {
  list-style-type: none;
  background-color: #303030;
  padding: 5px;
  margin-bottom: 2px;
}
.v-text-field--solo input {
  padding: 8px 0px;
}
</style>
