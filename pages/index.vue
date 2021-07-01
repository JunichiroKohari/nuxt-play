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
          <v-btn
            id="donwloadbtn"
            color="primary"
            nuxt
            @click="download"
          >
            download
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
      test:{},
      blobData: {}
    }
  },
  async mounted() {
    // const { data } = await axios.get('http://localhost/api/test')
    // const {data} = await axios.get('https://c57e447d-3719-4893-93d8-f589f3431417.mock.pstmn.io//v1/test')
    // const {data} = await axios.get('http://localhost/v1/test')
    // // console.log(data)
    // this.blobData = new Blob([data], { type: 'image/jpeg' })
    // document.getElementById("donwloadbtn").href = window.URL.createObjectURL(this.blobData);
    // this.test = data
  },
  methods: {
    download () {
      var fname = "test.jpeg"
        if (window.navigator.msSaveBlob) { 
            console.log("#-msSaveBlob")
            window.navigator.msSaveBlob(this.blobData, fname ); 
            window.navigator.msSaveOrOpenBlob(this.blobData, fname ); 
            const bloburl = window.URL.createObjectURL(this.blobData);
        } else {
            console.log("#-msSaveBlob-false")
            const bloburl = window.URL.createObjectURL(this.blobData);
            document.getElementById("donwloadbtn").href = bloburl;
            // console.log(document.getElementById("donwloadbtn").href)
            console.log(bloburl)
        } 
    }
  }
}
</script>
