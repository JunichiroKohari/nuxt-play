<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <div class="text-center">
        <logo />
        <vuetify-logo />
      </div>
      <v-card>
        <v-card-title class="headline">
          Welcome to the Vuetify + Nuxt.js template
        </v-card-title>
        <v-card-text>
          <p>Vuetify is a progressive Material Design component framework for Vue.js. It was designed to empower developers to create amazing applications.</p>
        </v-card-text>
        <v-card-actions>
          <v-spacer />
          <v-btn
            color="primary"
            nuxt
            to="/inspire"
          >
            Continue
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
import Logo from '~/components/Logo.vue'
import VuetifyLogo from '~/components/VuetifyLogo.vue'
import axios from 'axios'

export default {
  components: {
    Logo,
    VuetifyLogo
  },
  data () {
    return {
      test:{}
    }
  },
  async mounted() {
    // const { data } = await axios.get('http://localhost/api/test')
    const {data} = await axios.get('https://c57e447d-3719-4893-93d8-f589f3431417.mock.pstmn.io//v1/test')
    console.log(data)
    this.test = data
  }
}
</script>
