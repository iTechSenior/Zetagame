<template>
  <v-container id="p_users" fluid class="pr-0 ma-0">
    <v-layout row justify-space-between>
      <v-flex xs2>
        <v-text-field label="Enter User Name"></v-text-field>
      </v-flex>
      <v-flex xs2>
        <v-btn style="width:100%; font-size: 14px;" color="green">
          <v-icon>mdi-plus</v-icon>&nbsp;Add New User
        </v-btn>
      </v-flex>
    </v-layout>
    <v-layout row>
      <v-data-table
        :headers="headers"
        :items="users"
        class="elevation-1"
        style="width: 100%;"
        hide-headers
        hide-actions
      >
        <template v-slot:items="props">
          <td width="66%">
            <v-layout row>
              <v-flex style="max-width: 60px;">
                <v-layout
                  justify-center
                  align-center
                  fill-height
                  style="background-color: #161616;"
                >
                  <v-img
                    v-if="!!props.item.avatar"
                    :src="props.item.avatar"
                  ></v-img>
                  <v-icon v-if="!props.item.avatar" x-large>mdi-account</v-icon>
                </v-layout>
              </v-flex>
              <v-flex>
                <v-layout class="pl-3">
                  <v-flex xs12>{{ props.item.user_name }}</v-flex>
                </v-layout>
                <v-layout row>
                  <v-flex xs2>
                    <v-subheader style="justify-content: flex-end;"
                      >Sports:</v-subheader
                    >
                  </v-flex>
                  <v-flex
                    xs2
                    style="justify-content: start; align-items: center; display: flex;"
                  >
                    <v-chip label color="warning">{{
                      props.item.sports
                    }}</v-chip>
                  </v-flex>
                  <v-flex xs2>
                    <v-subheader style="justify-content: flex-end;"
                      >Casino:</v-subheader
                    >
                  </v-flex>
                  <v-flex
                    xs2
                    style="justify-content: start; align-items: center; display: flex;"
                  >
                    <v-chip label color="warning">
                      {{ props.item.casino }}
                    </v-chip>
                  </v-flex>
                  <v-flex xs2>
                    <v-subheader style="justify-content: flex-end;"
                      >Tombala:</v-subheader
                    >
                  </v-flex>
                  <v-flex
                    xs2
                    style="justify-content: start; align-items: center; display: flex;"
                  >
                    <v-chip label color="warning">
                      {{ props.item.tombala }}
                    </v-chip>
                  </v-flex>
                  <v-flex xs2>
                    <v-subheader style="justify-content: flex-end;"
                      >Betagames:</v-subheader
                    >
                  </v-flex>
                  <v-flex
                    xs2
                    style="justify-content: start; align-items: center; display: flex;"
                  >
                    <v-chip label color="warning">
                      {{ props.item.betagames }}
                    </v-chip>
                  </v-flex>
                </v-layout>
              </v-flex>
            </v-layout>
          </td>
          <td width="34%">
            <v-layout justify-end>{{ props.item.email }}</v-layout>
            <v-layout justify-end>
              Settings&nbsp;
              <v-icon>mdi-settings</v-icon>
            </v-layout>
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
      headers: [{ text: 'item' }],
      users: [
        {
          avatar: null,
          user_name: 'User Deneme1',
          sports: '6010.50 TL',
          casino: '10.50 TL',
          tombala: '6010.50 TL',
          betagames: '6010.50 TL',
          email: 'UserDeneme@mail.com'
        },
        {
          avatar: null,
          user_name: 'Bayi256',
          sports: '6010.50 TL',
          casino: '10.50 TL',
          tombala: '6010.50 TL',
          betagames: '6010.50 TL',
          email: 'Bayi256@mail.com'
        }
      ]
    }
  }
}
</script>

<style scoped>
table.v-table tbody td,
table.v-table tbody th,
table.v-table thead td,
table.v-table thead th {
  padding: 10px 12px !important;
}
.v-chip {
  color: white;
  font-size: 14px;
  font-weight: bold;
}
</style>
