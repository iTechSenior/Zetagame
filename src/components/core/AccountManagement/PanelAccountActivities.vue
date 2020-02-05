<template>
  <v-container id="p_activities" row fluid class="pr-0 ma-0">
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
          full-width
          min-width="290px"
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
        <v-btn color="success" style="width: 100%">Show Account History</v-btn>
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
          <td>{{ props.item.date_time }}</td>
          <td class="text-xs-left">{{ props.item.user_name }}</td>
          <td class="text-xs-left">{{ props.item.motion_type }}</td>
          <td class="text-xs-left">{{ props.item.old_credit }}</td>
          <td class="text-xs-left">{{ props.item.quantity }}</td>
          <td class="text-xs-left">{{ props.item.new_credit }}</td>
          <td class="text-xs-left">{{ props.item.note }}</td>
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
        {
          text: 'Date/Time',
          align: 'left',
          sortable: false,
          color: 'success',
          value: 'date_time'
        },
        { text: 'User Name', value: 'user_name', align: 'left' },
        { text: 'Motion Type', value: 'motion_type', align: 'left' },
        { text: 'Old Credit', value: 'old_credit', align: 'left' },
        { text: 'Quantity', value: 'quantity', align: 'left' },
        { text: 'New Credit', value: 'new_credit', align: 'left' },
        { text: 'Note', value: 'note', align: 'left' }
      ],
      activities: [
        {
          date_time: '27/03/07.15',
          user_name: 'Admin Test > Bayitest',
          motion_type: 'Kaybeden Kuponlar',
          old_credit: 120025,
          quantity: 120025,
          new_credit: 1848385,
          note: 'Lost Coupon Live 912197'
        },
        {
          date_time: '27/03/07.15',
          user_name: 'Admin Test > Bayitest',
          motion_type: 'Bakiye Cekme',
          old_credit: 120025,
          quantity: 120025,
          new_credit: 1848385,
          note: 'User Withdrawal'
        }
      ]
    }
  }
}
</script>

<style></style>
