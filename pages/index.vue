<template lang="pug">
  div
    nuxt-link(
      to="/users"
    ) Usres page
    br
    nuxt-link(
      to="/products"
    ) Products page
    br
    nuxt-link(
      to="/vuetify"
    ) Vuetify page
    br
    nuxt-link(
      to="/pug"
    ) Pug page

</template>

<script>
import axios from 'axios'

export default {
  components: {
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
