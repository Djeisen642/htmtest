<template>
  <v-layout row align-center justify-center>
    <v-flex xs12 sm5>
      <v-btn
          fixed
          dark
          fab
          bottom
          right
          color="primary"
          class="mb-5 mr-2"
          nuxt
          to="/addguest"
      >
        <v-icon>add</v-icon>
      </v-btn>
      <v-card>
        <v-card-title class="headline pb-0">Dashboard</v-card-title>
        <v-container
            fluid
            grid-list-lg
        >
          <v-layout row wrap>
            <v-flex>
              <v-card>
                <v-card-title primary-title>
                  <v-icon color="blue darken-2">contacts</v-icon>
                </v-card-title>
                <v-card-text>
                  <div class="display-2">{{contacts}}</div>
                </v-card-text>
                <v-divider></v-divider>
                <v-card-actions class="pa-3">
                  <div class="subheading">Total Contacts</div>
                </v-card-actions>
              </v-card>
            </v-flex>

            <v-flex xs12>
              <v-card>
                <v-card-title primary-title>
                  <v-icon color="purple darken-1">fa-wine-glass</v-icon>
                </v-card-title>
                <v-card-text>
                  <div class="display-2">{{oneStepCouples}}</div>
                </v-card-text>
                <v-divider></v-divider>
                <v-card-actions class="pa-3">
                  <div class="subheading">Couples given Holy Wine</div>
                </v-card-actions>
              </v-card>
            </v-flex>

            <v-flex xs12>
              <v-card>
                <v-card-title primary-title>
                  <v-icon color="red darken-1">fa-magic</v-icon>
                </v-card-title>
                <v-card-text>
                  <div class="display-2">{{threeStepCouples}}</div>
                </v-card-text>
                <v-divider></v-divider>
                <v-card-actions class="pa-3">
                  <div class="subheading">Couples completed Chastening Ceremony</div>
                </v-card-actions>
              </v-card>
            </v-flex>

          </v-layout>
        </v-container>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
  export default {
    data () {
      return {
        threeStepCouples: 0,
        oneStepCouples: 0,
        contacts: 0
      }
    },
    async created () {
      const response = await this.$axios.get('/persons/dashboard')
      this.threeStepCouples = response.data.threeStepCouplesCount
      this.oneStepCouples = response.data.oneStepCouplesCount
      this.contacts = response.data.contactsCount
    },
    computed: {
      threeStepCouplesProgress () {
        return this.threeStepCouples / 430 * 100
      }
    }
  }
</script>

<style scoped>

</style>
