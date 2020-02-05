<template>
  <v-container id="p_printer" fluid class="pr-0 ma-0">
    <v-form v-model="valid">
      <v-container class="ma-0" style="max-width: 800px;">
        <v-layout>
          <v-flex xs3>
            <v-subheader>Printer Mode:</v-subheader>
          </v-flex>
          <v-flex xs3>
            <v-autocomplete outline></v-autocomplete>
          </v-flex>
          <v-flex xs6>
            <v-btn color="success" class="ma-0 ml-5" style="height: 40px"
              >Preview</v-btn
            >
          </v-flex>
        </v-layout>
        <v-layout>
          <v-flex xs3>
            <v-subheader>Coupon Style:</v-subheader>
          </v-flex>
          <v-flex xs3>
            <v-autocomplete outline></v-autocomplete>
          </v-flex>
        </v-layout>
        <v-layout>
          <v-flex xs3>
            <v-subheader>% Deduction:</v-subheader>
          </v-flex>
          <v-flex xs3>
            <v-text-field outline></v-text-field>
          </v-flex>
        </v-layout>
        <v-layout>
          <v-flex xs3>
            <v-subheader>Show Coupon Interruption:</v-subheader>
          </v-flex>
          <v-flex xs3>
            <v-autocomplete outline></v-autocomplete>
          </v-flex>
          <v-flex xs6>
            <v-subheader style="color: green"
              >* Commission breaks the coupon!</v-subheader
            >
          </v-flex>
        </v-layout>
        <v-layout>
          <v-flex xs3>
            <v-subheader>Koupon Yer Alacak Notlar:</v-subheader>
          </v-flex>
          <v-flex xs3>
            <v-textarea id="textarea_coupon" outline></v-textarea>
          </v-flex>
        </v-layout>
        <v-layout>
          <v-flex xs3>
            <v-subheader>Currency:</v-subheader>
          </v-flex>
          <v-flex xs3>
            <v-autocomplete outline></v-autocomplete>
          </v-flex>
          <v-flex xs6>
            <v-subheader style="color: green"
              >* Prints the specified currency (£, €, $, TL)</v-subheader
            >
          </v-flex>
        </v-layout>
        <v-layout>
          <v-flex xs3></v-flex>
          <v-flex xs3></v-flex>
          <v-flex xs6>
            <v-btn color="green" class="ml-5">Update Settings</v-btn>
          </v-flex>
        </v-layout>
      </v-container>
    </v-form>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      valid: true
    }
  }
}
</script>

<style>
textarea_coupon textarea {
  margin-top: 5px;
}
</style>
