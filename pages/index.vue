<template>
  <v-main align="center" justify="center">
    <v-container class="fill-height" fluid>
      <v-row
        align="center"
        justify="center"
        style="margin-top:200px;"
        v-if="showLogin"
      >
        <v-col cols="12" sm="8" md="4">
          <v-card class="elevation-12">
            <v-toolbar color="primary" justify="center" dark flat>
              <v-toolbar-title>Login</v-toolbar-title>
              <v-spacer></v-spacer>
            </v-toolbar>
            <p
              v-bind:class="{
                successMessage: successMessage,
                errorMessage: errorMessage
              }"
            >
              <v-card-text>
                <v-form>
                  <v-text-field
                    label="Username/Email"
                    name="login"
                    append-icon="fa fa-user"
                    type="text"
                  ></v-text-field>

                  <v-text-field
                    id="password"
                    label="Password"
                    name="password"
                    :append-icon="showPassword ? 'fa-eye' : 'fa-eye-slash'"
                    :type="showPassword ? 'text' : 'password'"
                    @click:append="showPassword = !showPassword"
                  ></v-text-field>
                  <v-flex style="text-align:right;">
                    <label class="forgotPassword">
                      <a href="#" @click="openForgot()">Forgot password?</a>
                    </label>
                  </v-flex>
                </v-form>
              </v-card-text>
              <v-card-actions>
                <v-btn color="primary" @click="openRegister()">Register</v-btn>
                <v-spacer></v-spacer>
                <v-btn color="primary" @click="openLogin()">Login</v-btn>
              </v-card-actions>
            </p></v-card
          >
        </v-col>
      </v-row>

      <!-- Register v-card -->
      <v-row
        align="center"
        justify="center"
        style="margin-top:200px;"
        v-if="showRegister"
      >
        <v-col cols="12" sm="8" md="4">
          <v-card class="elevation-12">
            <v-toolbar color="primary" justify="center" dark flat>
              <v-toolbar-title>Register</v-toolbar-title>
              <v-spacer></v-spacer>
            </v-toolbar>
            <p
              v-bind:class="{
                successMessage: successMessage,
                errorMessage: errorMessage
              }"
            >
              <v-card-text>
                <v-form>
                  <v-text-field
                    label="Username/Email"
                    name="login"
                    append-icon="fa fa-user"
                    type="text"
                  ></v-text-field>

                  <v-text-field
                    label="Email"
                    name="email"
                    type="email"
                  ></v-text-field>

                  <v-text-field
                    id="password"
                    label="Password"
                    name="password"
                    :append-icon="showPassword ? 'fa-eye' : 'fa-eye-slash'"
                    :type="showPassword ? 'text' : 'password'"
                    @click:append="showPassword = !showPassword"
                  ></v-text-field>

                  <v-text-field
                    id="confirmPassword"
                    label="Confirm Password"
                    name="confirmPassword"
                    :append-icon="showPassword ? 'fa-eye' : 'fa-eye-slash'"
                    :type="showPassword ? 'text' : 'password'"
                    @click:append="showPassword = !showPassword"
                  ></v-text-field>

                  <v-flex style="text-align:right;">
                    <label class="forgotPassword">
                      <a href="#" @click="openForgot()">Forgot password?</a>
                    </label>
                  </v-flex>
                </v-form>
              </v-card-text>
              <v-card-actions>
                <v-btn color="primary" @click="openLogin()">Login</v-btn>
                <v-spacer></v-spacer>
                <v-btn color="primary" @click="openRegister()">Register</v-btn>
              </v-card-actions>
            </p></v-card
          >
        </v-col>
      </v-row>

      <!-- Forgot password v-card-->
      <v-row
        align="center"
        justify="center"
        style="margin-top:200px;"
        v-if="showForgot"
      >
        <v-col cols="12" sm="8" md="4">
          <v-card class="elevation-12">
            <v-toolbar color="primary" justify="center" dark flat>
              <v-toolbar-title>Forgot Password</v-toolbar-title>
              <v-spacer></v-spacer>
            </v-toolbar>
            <p>
              No problem! Just fill in the email below and we'll send you
              password reset instructions!
            </p>
            <p
              v-bind:class="{
                successMessage: successMessage,
                errorMessage: errorMessage
              }"
            >
              {{ this.errorMessage }} {{ this.successMessage }}
            </p>
            <v-card-text>
              <v-form>
                <v-text-field
                  label="Email"
                  name="email"
                  type="email"
                ></v-text-field>

                <v-text-field
                  label="OTP"
                  name="email"
                  type="email"
                ></v-text-field>

                <v-text-field
                  id="password"
                  label="Password"
                  name="password"
                  :append-icon="showPassword ? 'fa-eye' : 'fa-eye-slash'"
                  :type="showPassword ? 'text' : 'password'"
                  @click:append="showPassword = !showPassword"
                ></v-text-field>

                <v-text-field
                  id="confirmPassword"
                  label="Confirm Password"
                  name="confirmPassword"
                  :append-icon="showPassword ? 'fa-eye' : 'fa-eye-slash'"
                  :type="showPassword ? 'text' : 'password'"
                  @click:append="showPassword = !showPassword"
                ></v-text-field>

                <v-flex style="text-align:right;"> </v-flex>
              </v-form>
            </v-card-text>
            <v-card-actions>
              <v-btn color="primary" @click="openLogin()">Login</v-btn>
              <v-spacer></v-spacer>
              <v-btn color="primary">Reset</v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </v-main>
</template>

<script>
import Logo from "~/components/Logo.vue";
import VuetifyLogo from "~/components/VuetifyLogo.vue";

export default {
  data() {
    return {
      showPassword: false,
      showLogin: true,
      showRegister: false,
      showForgot: false,
      errorMessage: "",
      successMessage: ""
    };
  },
  components: {
    Logo,
    VuetifyLogo
  },
  methods: {
    openLogin() {
      this.showLogin = true;
      this.showRegister = false;
      this.showForgot = false;
    },
    openRegister() {
      this.showLogin = false;
      this.showRegister = true;
      this.showForgot = false;
    },
    openForgot() {
      this.showLogin = false;
      this.showRegister = false;
      this.showForgot = true;
    }
  }
};
</script>
