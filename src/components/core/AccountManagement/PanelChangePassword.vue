<template>
  <v-container id="p_chpwd" fluid class="pr-0 ma-0">
    <v-form v-model="valid">
      <v-container class="ma-0" style="max-width: 800px;">
        <v-layout>
          <v-flex xs3>
            <v-subheader>Old Password:</v-subheader>
          </v-flex>
          <v-flex xs3>
            <v-text-field outline></v-text-field>
          </v-flex>
        </v-layout>
        <v-layout>
          <v-flex xs3>
            <v-subheader>New Password:</v-subheader>
          </v-flex>
          <v-flex xs3>
            <v-text-field outline></v-text-field>
          </v-flex>
        </v-layout>
        <v-layout>
          <v-flex xs3>
            <v-subheader>New Password Repeat:</v-subheader>
          </v-flex>
          <v-flex xs3>
            <v-text-field outline></v-text-field>
          </v-flex>
        </v-layout>
        <v-layout>
          <v-flex xs3></v-flex>
          <v-flex xs3></v-flex>
          <v-flex xs3>
            <v-btn color="success">Change Password</v-btn>
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

<style scoped></style>
