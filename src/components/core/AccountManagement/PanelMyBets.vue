<template>
  <v-container id="p_mybets" fluid class="pr-0 ma-0">
    <v-layout row class="mb-4 mt-2">
      <v-flex xs3 class="mr-5">
        <v-layout row class="pb-2" style="border-bottom: 4px solid green">
          <v-flex xs8 class="text-xs-center">Winner Coupons</v-flex>
          <v-flex xs4 class="text-xs-center">12 Adet</v-flex>
        </v-layout>
      </v-flex>
      <v-flex xs3 class="mr-5">
        <v-layout row class="pb-2" style="border-bottom: 4px solid red">
          <v-flex xs8 class="text-xs-center">Losing Coupons</v-flex>
          <v-flex xs4 class="text-xs-center">12 Adet</v-flex>
        </v-layout>
      </v-flex>
      <v-flex xs3 class="mr-5">
        <v-layout row class="pb-2" style="border-bottom: 4px solid yellow">
          <v-flex xs8 class="text-xs-center">Pending Coupons</v-flex>
          <v-flex xs4 class="text-xs-center">12 Adet</v-flex>
        </v-layout>
      </v-flex>
      <v-flex xs3>
        <v-layout row class="pb-2" style="border-bottom: 4px solid blue">
          <v-flex xs8 class="text-xs-center">Returned Coupons</v-flex>
          <v-flex xs4 class="text-xs-center">12 Adet</v-flex>
        </v-layout>
      </v-flex>
    </v-layout>
    <v-layout row>
      <v-flex xs2>
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
              label="Staring Date"
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
      <v-flex xs2 class="pr-2">
        <v-autocomplete
          :items="items"
          autocomplete
          label="Coupon Type"
        ></v-autocomplete>
      </v-flex>
      <v-flex xs1 class="pr-2">
        <v-text-field label="Coupon Id"></v-text-field>
      </v-flex>
      <v-flex xs2 class="pr-2">
        <v-autocomplete
          :items="items"
          autocomplete
          label="Coupon Result"
        ></v-autocomplete>
      </v-flex>
      <v-flex xs1 class>
        <v-btn color="success" style="width: 100%">Get</v-btn>
      </v-flex>
    </v-layout>
    <v-layout row>
      <v-data-table
        :headers="headers"
        :items="activities"
        class="elevation-1"
        style="width: 100%;"
      >
        <template v-slot:items="props">
          <td>{{ props.item.coupon_id }}</td>
          <td>{{ props.item.user_name }}</td>
          <td>{{ props.item.date_time }}</td>
          <td>{{ props.item.finished }}</td>
          <td>{{ props.item.invested }}</td>
          <td>{{ props.item.oran }}</td>
          <td>{{ props.item.rate }}</td>
          <td>{{ props.item.note }}</td>
          <td>{{ props.item.tip }}</td>
          <td>{{ props.item.status }}</td>
          <td>
            <v-btn flat icon class="ma-0">
              <v-icon medium>mdi-magnify</v-icon>
            </v-btn>
            <v-btn flat icon class="ma-0">
              <v-icon medium>mdi-printer-settings</v-icon>
            </v-btn>
            <v-btn
              v-if="props.item.status == 'Waiting'"
              flat
              icon
              color="error"
              class="ma-0"
            >
              <v-icon medium>mdi-close</v-icon>
            </v-btn>
          </td>
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
        { text: 'Coupon Id', value: 'coupon_id', align: 'left' },
        { text: 'User Name', value: 'user_name', align: 'left' },
        { text: 'Date / Time', value: 'date_time', align: 'left' },
        { text: 'Finished', value: 'finished', align: 'left' },
        { text: 'Invested', value: 'invested', align: 'left' },
        { text: 'Oran', value: 'oran', align: 'left' },
        { text: 'Rate', value: 'rate', align: 'left' },
        { text: 'Note', value: 'note', align: 'left' },
        { text: 'Tip', value: 'tip', align: 'left' },
        { text: 'Status', value: 'status', align: 'left' },
        { text: 'Action', value: 'action', align: 'left' }
      ],
      activities: [
        {
          coupon_id: '912126',
          user_name: 'Admin Test > Bayitest',
          date_time: '27/03/07.15',
          finished: '1/1',
          invested: 120025,
          oran: 1.54,
          rate: 1848385,
          note: 'Lorem ipsum',
          tip: 'Tekli',
          status: 'Waiting',
          action: ''
        },
        {
          coupon_id: '912126',
          user_name: 'Admin Test > Lorem ipsum',
          date_time: '27/03/07.15',
          finished: '1/1',
          invested: 1025,
          oran: 1.54,
          rate: 108385,
          note: 'Lorem ipsum',
          tip: 'Tekli',
          status: 'Won',
          action: ''
        },
        {
          coupon_id: '912126',
          user_name: 'Admin Test > Deneme 01',
          date_time: '27/03/07.15',
          finished: '1/1',
          invested: 120025,
          oran: 1.54,
          rate: 1848385,
          note: 'Lorem ipsum',
          tip: 'Tekli',
          status: 'Lost',
          action: ''
        }
      ]
    }
  }
}
</script>

<style scoped></style>
