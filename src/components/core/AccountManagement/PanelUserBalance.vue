<template>
  <v-container id="p_mybets" fluid class="pr-0 ma-0">
    <v-layout row>
      <v-flex xs2>
        <v-text-field label="Enter User Name"></v-text-field>
      </v-flex>
    </v-layout>
    <v-layout row>
      <v-data-table
        :headers="headers"
        :items="balances"
        class="elevation-1"
        style="width: 100%;"
      >
        <template v-slot:items="props">
          <td>{{ props.item.user_name }}</td>
          <td>{{ props.item.email }}</td>
          <td>{{ props.item.balance }}</td>
          <td>{{ props.item.casino }}</td>
          <td>
            <v-autocomplete>{{ props.item.medicine }}</v-autocomplete>
          </td>
          <td>
            <v-text-field>{{ props.item.quantity }}</v-text-field>
          </td>
          <td>
            <v-text-field>{{ props.item.note }}</v-text-field>
          </td>
          <td>
            <v-btn class="ma-0" color="success" style="width: 100%">
              <v-icon medium>mdi-update</v-icon>&nbsp;Update
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
      selected: [],
      headers: [
        { text: 'User Name', value: 'user_name' },
        { text: 'Email', value: 'email' },
        { text: 'Balance', value: 'balance' },
        { text: 'Casino', value: 'casino' },
        { text: 'Medicine', value: 'medicine' },
        { text: 'Quantity', value: 'quantity' },
        { text: 'Note', value: 'note' }
      ],
      balances: [
        {
          user_name: 'Admin Test Deneme',
          email: 'admintest@mail.com',
          balance: '162000.00 TL',
          casino: '152000.00 TL',
          medicine: null,
          quantity: null,
          note: null
        },
        {
          user_name: 'Admin Test Deneme',
          email: 'admintest@mail.com',
          balance: '162000.00 TL',
          casino: '152000.00 TL',
          medicine: null,
          quantity: null,
          note: null
        },
        {
          user_name: 'Admin Test Deneme',
          email: 'admintest@mail.com',
          balance: '162000.00 TL',
          casino: '152000.00 TL',
          medicine: null,
          quantity: null,
          note: null
        }
      ]
    }
  }
}
</script>

<style scoped></style>
