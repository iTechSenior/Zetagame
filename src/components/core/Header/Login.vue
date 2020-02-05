<template>
  <v-layout class="pt-3 login" row>
    <v-flex xs3 class="text-lg-right pr-4">
      <span>Welcome Lorem</span>
    </v-flex>
    <v-flex xs3 pr-2>
      <v-autocomplete label solo></v-autocomplete>
    </v-flex>
    <v-flex xs3 pr-2>
      <v-autocomplete label solo></v-autocomplete>
    </v-flex>
    <v-flex xs1 pr-2>
      <v-btn color="success" block>My Bets</v-btn>
    </v-flex>
    <v-flex xs1 pr-2>
      <v-btn color="error" block>Exit</v-btn>
    </v-flex>
    <v-flex xs2 pr-2>
      <v-autocomplete label solo></v-autocomplete>
    </v-flex>
  </v-layout>
</template>

<script>
export default {}
</script>
