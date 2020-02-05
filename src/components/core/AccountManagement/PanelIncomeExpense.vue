<template>
  <v-container id="p_mybets" fluid class="pr-0 ma-0">
    <v-layout row class="mb-4 mt-2">
      <v-flex xs3 class="mr-5">
        <v-layout row class="pb-2 mb-2" style="border-bottom: 4px solid green">
          <v-flex xs8 class="text-xs-center">Amount Played</v-flex>
          <v-flex xs4 class="text-xs-center">12 Piece</v-flex>
        </v-layout>
        <v-layout justify-center>25.00 TL</v-layout>
      </v-flex>
      <v-flex xs3 class="mr-5">
        <v-layout row class="pb-2 mb-2" style="border-bottom: 4px solid red">
          <v-flex xs8 class="text-xs-center">Winner Amount</v-flex>
          <v-flex xs4 class="text-xs-center">5 Piece</v-flex>
        </v-layout>
        <v-layout justify-center>25.00 TL</v-layout>
      </v-flex>
      <v-flex xs3 class="mr-5">
        <v-layout row class="pb-2 mb-2" style="border-bottom: 4px solid yellow">
          <v-flex xs8 class="text-xs-center">Losing</v-flex>
          <v-flex xs4 class="text-xs-center">12 Piece</v-flex>
        </v-layout>
        <v-layout justify-center>00.00 TL</v-layout>
      </v-flex>
      <v-flex xs3>
        <v-layout row class="pb-2 mb-2" style="border-bottom: 4px solid blue">
          <v-flex xs8 class="text-xs-center">Pending Amount</v-flex>
          <v-flex xs4 class="text-xs-center">12 Piece</v-flex>
        </v-layout>
        <v-layout justify-center>00.00 TL</v-layout>
      </v-flex>
    </v-layout>
    <v-layout row>
      <v-flex xs3>
        <v-autocomplete
          :items="items"
          autocomplete
          label="Dealer Name"
        ></v-autocomplete>
      </v-flex>
      <v-flex xs2 class="pl-2 pr-2">
        <v-menu
          v-model="menu1"
          :close-on-content-click="false"
          :nudge-right="40"
          lazy
          transition="scale-transition"
          offset-y
        >
          <template v-slot:activator="{ on }">
            <v-text-field
              v-model="date"
              label="Starting Date"
              prepend-icon="mdi-calendar"
              readonly
              v-on="on"
            ></v-text-field>
          </template>
          <v-date-picker v-model="date" @input="menu1 = false"></v-date-picker>
        </v-menu>
      </v-flex>
      <v-flex xs2 class="pl-2 pr-2">
        <v-menu
          v-model="menu2"
          :close-on-content-click="false"
          :nudge-right="40"
          lazy
          transition="scale-transition"
          offset-y
        >
          <template v-slot:activator="{ on }">
            <v-text-field
              v-model="date"
              label="Date of Completion"
              prepend-icon="mdi-calendar"
              readonly
              v-on="on"
            ></v-text-field>
          </template>
          <v-date-picker v-model="date" @input="menu2 = false"></v-date-picker>
        </v-menu>
      </v-flex>
      <v-flex xs3>
        <v-autocomplete
          :items="items"
          autocomplete
          label="Movement Type"
        ></v-autocomplete>
      </v-flex>
      <v-flex xs2 class="pl-3">
        <v-btn color="success" style="width: 100%">List Report</v-btn>
      </v-flex>
    </v-layout>
    <v-layout row>
      <v-data-table
        :headers="headers"
        :items="list"
        class="elevation-1"
        style="width: 100%;"
      >
        <template v-slot:items="props">
          <td>{{ props.item.user_name }}</td>
          <td>
            <span style="color: yellow">{{ props.item.amount_played }}</span>
          </td>
          <td>
            <span style="color: green">{{ props.item.winner_amount }}</span>
          </td>
          <td>
            <span style="color: red">{{ props.item.losing_amount }}</span>
          </td>
          <td>
            <span style="color: blue">{{ props.item.pending_amount }}</span>
          </td>
          <td>{{ props.item.net_remaining }}</td>
          <td>{{ props.item.type_of_agreement }}</td>
          <td>{{ props.item.agreement_rate }}</td>
          <td>{{ props.item.commission }}</td>
        </template>
      </v-data-table>
    </v-layout>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      date: new Date().toISOString().substr(0, 10),
      menu1: false,
      menu2: false,
      items: [],
      headers: [
        { text: 'User Name', value: 'user_name', align: 'left' },
        { text: 'Amount Played', value: 'winner_amount', align: 'left' },
        { text: 'Winner Amount', value: 'winner_amount', align: 'left' },
        { text: 'Losing Amount', value: 'losing_amount', align: 'left' },
        { text: 'Pending Amount', value: 'pending_amount', align: 'left' },
        { text: 'Net Remaining', value: 'net_remaining', align: 'left' },
        {
          text: 'Type of Agreement',
          value: 'type_of_agreement',
          align: 'left'
        },
        { text: 'Agreement Rate', value: 'agreement_rate', align: 'left' },
        { text: 'Commission', value: 'commission', align: 'left' }
      ],
      list: [
        {
          user_name: 'Admin Test Deneme',
          amount_played: '152000.00 TL',
          winner_amount: '152000.00 TL',
          losing_amount: '152000.00 TL',
          pending_amount: '152000.00 TL',
          net_remaining: '152000.00 TL',
          type_of_agreement: 'No Commission',
          agreement_rate: 0,
          commission: '0.00'
        },
        {
          user_name: 'Admin Test Deneme2',
          amount_played: '2000.00 TL',
          winner_amount: '2000.00 TL',
          losing_amount: '2000.00 TL',
          pending_amount: '2000.00 TL',
          net_remaining: '2000.00 TL',
          type_of_agreement: 'No Commission',
          agreement_rate: 0,
          commission: '0.00'
        },
        {
          user_name: 'Admin Test Deneme',
          amount_played: '152000.00 TL',
          winner_amount: '152000.00 TL',
          losing_amount: '152000.00 TL',
          pending_amount: '152000.00 TL',
          net_remaining: '152000.00 TL',
          type_of_agreement: 'No Commission',
          agreement_rate: 0,
          commission: '0.00'
        },
        {
          user_name: 'Toplam',
          amount_played: '152000.00 TL',
          winner_amount: '152000.00 TL',
          losing_amount: '152000.00 TL',
          pending_amount: '152000.00 TL',
          net_remaining: '152000.00 TL',
          type_of_agreement: '-',
          agreement_rate: '-',
          commission: '0.00'
        }
      ]
    }
  }
}
</script>

<style scoped></style>
