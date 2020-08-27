<template>
  <v-app>
    <v-app-bar
      :app="$route.name == 'index' ? false : true"
      fixed
      color="black"
      class="navbar"
      dark
      mb-5
      dense     >
      <v-toolbar-title>
        <v-btn to="/" text color="transparent ">
          <v-img width="130" src="/logo/logo.png"></v-img>
        </v-btn>
      </v-toolbar-title>

      <v-spacer />

      <template v-for="(item, index) in menu">
        <v-btn
          :text="item.text"
          :rounded="true"
          :outlined="false"
          color="light-blue"
          :key="index"
          :to="item.to"
          class="mx-2 register"
        >
          <v-icon left>{{ item.icon }}</v-icon>
          &nbsp;{{ item.title }}
        </v-btn>
      </template>
    </v-app-bar>

      <!-- <div v-if="GetUserData">
        <v-list flat>
          <v-list-item class="px-0">
            <router-link to="/profile">
              <v-list-item-avatar class="mr-0" to="/profile">
                <img :src="this.defaultImage" :alt="GetUserData.username" />
              </v-list-item-avatar>
            </router-link>
            <v-menu offset-y>
              <template v-slot:activator="{ attrs, on }">
                <v-list-item-content>
                  <v-list-item-title
                    class="white--text ma-4 "
                    v-bind="attrs"
                    v-on="on"
                  >
                  Ritesh Naik
                    <span v-if="GetUserData.first_name">
                      {{ GetUserData.first_name.substring(0, 8) }}
                      {{ GetUserData.last_name.substring(0, 8) }}
                      </span>
                    
                    <span v-if="!GetUserData.first_name">
                      {{ GetUserData.username.substring(0, 8) }}
                    </span>
                  </v-list-item-title>
                </v-list-item-content>
              </template>
              <v-list>
                <v-list-item link class="menuList" to="/profile">
                  <v-list-item-title>
                    My Account
                  </v-list-item-title>
                </v-list-item>
                <v-list-item
                  link
                  class="menuList"
                  to="/profile/change_password"
                >
                  <v-list-item-title>
                    Change Password
                  </v-list-item-title>
                </v-list-item>
                <v-list-item link class="menuList" >
                  <v-list-item-title>
                    Logout
                  </v-list-item-title>
                </v-list-item>
              </v-list>
            </v-menu>

            <v-list-item-action>
              <v-icon size="15">{{
                $route.name === "profile"
                  ? "far fa-chevron-up"
                  : "far fa-chevron-down"
              }}</v-icon>
            </v-list-item-action>
          </v-list-item>
        </v-list>
      </div> -->
    <!-- Ending Login Form -->
    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>
    <v-footer :absolute="!fixed" app>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
import json from "~/json/items";
import Login from "../components/desktop/login";
import Register from "../components/desktop/register";
import forgotPassword from "../components/desktop/forgotPassword";

export default {
  data() {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      menu: json.menu,
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: "Ritesh Instagram",
      defaultImage: "../default.jpg",
      renderLogin: false,
      renderRegister: false,
      renderForgot: false,
      forgotPasswordDialog: false,
      loginDialog: false,
      registerDialog: false,
      userData: []
    };
  },
  components: {
    Login,
    Register,
    forgotPassword
  },
  methods: {
    // Force Render Login/Regisrer and Forgot Component
    forceRerender() {
      this.renderLogin = false;
      this.renderRegister = false;
      this.renderForgot = false;
      this.$nextTick(() => {
        this.renderLogin = true;
        this.renderRegister = true;
        this.renderForgot = true;
      });
    },
    // Open Register Form
    openRegisterForm() {
      this.forceRerender();
      this.registerDialog = true;
    },
    //openLogin Form
    openLoginForm() {
      this.forceRerender();
      this.loginDialog = true;
    },
    // Close Register Screen
    closeRegister() {
      this.registerDialog = false;
    },
    closeLogin() {
      this.loginDialog = false;
    },
    // Close Login Screen
    closeForgot() {
      this.forgotPasswordDialog = false;
    },
    // Show Register Form
    showRegisterDialog() {
      this.loginDialog = false;
      this.registerDialog = true;
    },
    // Show Login Form
    showLoginDialog() {
      this.registerDialog = false;
      this.loginDialog = true;
    },
    // Show Forgot Password Popup
    showForgotDialog() {
      this.forgotPasswordDialog = true;
      this.loginDialog = false;
    }
  }
};
</script>
<style scoped>
.menubtn {
  text-color: #ffffff;
}
</style>
