<template>
  <v-layout row height="10px;" class="deposit hidden-sm-and-down">
    <v-flex xs3 pr-2>
      <v-autocomplete label solo></v-autocomplete>
    </v-flex>
    <v-flex xs4 pr-2>
      <v-autocomplete label solo></v-autocomplete>
    </v-flex>
    <v-flex xs2 pr-2>
      <v-text-field label solo></v-text-field>
    </v-flex>
    <v-flex xs1 pr-2>
      <v-btn color="success" block>Deposit</v-btn>
    </v-flex>
    <v-flex xs3 pr-2>&nbsp;</v-flex>
  </v-layout>
</template>

<script>
export default {}
</script>
