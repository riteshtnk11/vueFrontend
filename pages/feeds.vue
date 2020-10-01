<template>
  <v-layout>
    <v-flex class="text-center">
      <img src="/v.png" alt="Vuetify.js" class="mb-5" />

      <v-row align="center" justify="center">
        <v-col cols="12" sm="8" md="4">
          <v-card>
            <v-row>
              <v-flex md2 lg2 sm2 pt-5 pl-2>
                <img class="pimage" src="/v.png" />
              </v-flex>
              <v-flex md8 lg9 sm8 pt-3 pl-3>
                <v-layout mt-1>
                  <v-text-field
                    placeholder="What's on your mind?"
                    outlined
                    rounded
                  >
                  </v-text-field>
                </v-layout>
              </v-flex>
            </v-row>
            <v-card-actions>
              <v-btn color="primary"
                ><v-icon>fas fa-image </v-icon> Photo/Video</v-btn
              >
              <v-spacer></v-spacer>
              <v-btn style="text-align:right;" color="primary">Post</v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>

      <v-row align="center" justify="center">
        <v-col cols="12" sm="8" md="4">
          <v-card>
            <v-row mt-5>
              <v-flex md2 lg2 sm2 pt-2 pl-2>
                <img class="pimage" src="/v.png" />
              </v-flex>
              <v-flex md8 lg9 sm8 pt-3 pl-3>
                <v-layout mt-1>
                  User name <v-spacer></v-spacer>
                  <v-icon right>fa fa-ellipsis-h</v-icon>
                </v-layout>
              </v-flex>
            </v-row>
            <v-row>
              <v-flex>
                <img src="/v.png" />
              </v-flex>
            </v-row>
            <v-card-actions>
              <v-row>
                <v-flex>
                  <v-icon left @click="openRegister()"
                    >far fa-heart fa-2x</v-icon
                  >
                  <!-- <v-icon left>fa fa-heart fa-2x</v-icon>  -->
                  <v-icon left>far fa-comment fa-2x</v-icon>
                  <v-icon left>far fa-share fa-2x</v-icon>
                </v-flex>
                <v-spacer></v-spacer><v-spacer></v-spacer>
                <v-flex>
                  <v-icon right>far fa-bookmark fa-2x</v-icon>
                </v-flex>
              </v-row>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </v-flex>
  </v-layout>
</template>
<script>
export default {
  methods: {
    openRegister() {
      console.log("Hello");
    }
  }
};
</script>
<style scoped>
.pimage {
  height: 50px;
  border: 2px solid #dddddd;
  border-radius: 180px;
}
</style>
