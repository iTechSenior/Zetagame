<template>
  <v-app dark>
    <v-content>
      <div id="core-view">
        <v-fade-transition mode="out-in">
          <div class="bg-login">
            <v-layout row justify-center align-center style="height: 100vh">
              <v-flex
                xs3
                style="margin-top: calc(-100vh / 5); min-width: 400px;"
              >
                <v-card class="pl-2 pt-2 pr-2">
                  <v-form
                    id="signinForm"
                    ref="form"
                    v-model="valid"
                    lazy-validation
                  >
                    <v-container>
                      <v-text-field
                        v-model="username"
                        :rules="usernameRules"
                        :label="$t('Login.user_name')"
                        required
                        solo
                        background-color="#181818"
                      ></v-text-field>
                      <v-text-field
                        v-model="password"
                        :rules="passwordRules"
                        :label="$t('Login.user_password')"
                        required
                        solo
                        background-color="#181818"
                      ></v-text-field>
                      <v-layout justify-space-between class="ma-0" height="50">
                        <v-flex xs4 class="pa-0">
                          <v-autocomplete
                            v-model="language"
                            :items="langList"
                            :rules="[v => !!v || 'Language is required']"
                            background-color="#181818"
                            placeholder="Language"
                            height="30"
                            required
                            class="pa-0 ma-0"
                          ></v-autocomplete>
                        </v-flex>
                        <v-flex xs3 class="pa-0">
                          <v-btn
                            color="green"
                            style="width: 100%;"
                            class="ma-0"
                            @click="signin"
                            >{{ $t('Login.sign_in') }}</v-btn
                          >
                        </v-flex>
                      </v-layout>
                      <span style="color: #f55a4e;">{{ message }}</span>
                    </v-container>
                  </v-form>
                </v-card>
              </v-flex>
            </v-layout>
          </div>
        </v-fade-transition>
      </div>
    </v-content>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      valid: true,
      username: '',
      usernameRules: [
        v => !!v || 'User name is required',
        v =>
          (v && v.length <= 25) || 'User name must be less than 25 characters'
      ],
      password: '',
      passwordRules: [
        v => !!v || 'Password is required',
        v => (v && v.length >= 8) || 'Password must be more than 8 characters'
      ],
      language: '',
      langList: ['English', 'Turkish'],
      message: ''
    }
  },
  methods: {
    signin() {
      if (this.$refs.form.validate()) {
        // here call signin API call.
        // when the result is OK, go to homepage.
        let validUser = true
        // let validUser = false
        if (validUser) {
          this.$router.push('/account-management')
        } else {
          this.message = 'Incorrect User name or password!'
        }
      }
    }
  }
}
</script>

<style>
#signinForm .v-input__control {
  min-height: 20px;
}
#signinForm .v-btn {
  padding: 5px;
}
</style>

<style scoped>
.bg-login {
  background: url('/img/bg_login.png');
  min-height: 100vh;
}

#core-view {
  padding-bottom: unset;
}
</style>
