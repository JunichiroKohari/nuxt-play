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
    v-btn(
      @click="buildingDocument = !buildingDocument"
    ) pdf
    br
    pdf(
      v-if="buildingDocument"
      src="https://s3.ap-northeast-1.amazonaws.com/www.awsbookexample001.com/%E8%A8%98%E5%B8%B3%E4%BB%A3%E8%A1%8C%E3%83%9E%E3%83%8B%E3%83%A5%E3%82%A2%E3%83%ABVer7.0.pdf?response-content-disposition=inline&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEEQaDmFwLW5vcnRoZWFzdC0xIkcwRQIhANRCRmBijW%2Fs%2F2iLDDvb41z8wV%2BIThH0BYkUD26djRe8AiAg3VpxTWjO%2FB%2F9hNjhkxm64CscDBLhG1Vd%2FfaY3qDOjCr6AgguEAIaDDEzMjIxNzgzNTc4MiIMPR7wjdaFg4MG4MbRKtcCtfJ7%2BeBeZzdFD%2BsZ2D71JHpfMDQo5860GfdwTJ7rJJMVIm%2F9ssGYU%2FwXHwXbHoLEr%2FCjRnLMkZc7Fq%2Fd93dHWvSoL9a%2Fp%2FSA29n0VRQDTruzjHmEjOSWjU%2FXh7LyljQmWi0VUIrcy%2BatJ5NIp1fVoIE9ePkw1kBOjW3EHacdpiHzuG4W8laN9dvBV%2FT%2FGGCMdc06mDnaRJd34V9pSbqoIg8RzNrbVgnV8CT7XHaFJWgrQz8B%2FJzOhxKOINxUGjiA2lDvIj1y9PDlXZ0%2FrmllEGwRUMmYCc6%2BlEF5A1gvo2IBZwqQelW05Dex1dCG0UCd18tJqYe8eFOMdR%2BawI%2FJJ%2FPPhNMdmBPIE6duxQGaCouv785A3IGQGIBNAxlF4XBmYCOblheZarJQXBSxBtNMr7A2O8ly5rFaMxSpE2%2BKgagZr3YepEVAcwdHx0JS9ddklsqCmXMXuzDL84uHBjqzAgEaXkEGwJvZd8DejpBLozliUbbv%2FCgbvuTZcKqsGI%2FNRVb1GdKIyzMtQANifG%2BSSPHtK5J9jzy%2FEs20m%2BBZvRzd%2F0Y%2FZbYpGXWYPpW0dtAg6ttuPYsOm7NHz2LA8wPK%2BpQ5ytWinH1OXaPff4YEaGvE989Z9BeBMtS4YeCM2vRJsP5nIoZ%2BcVedkGtjPQdPEFC2z6YhF8x1%2F5ouhWBMlpa%2F4P%2BkhcwHERwOetEYhF5PbA2W451B41uNsH6TrKLNjT3g7zTEjJPEFS8UJyJVOyUH7XlS0pIN3IsoaKy52BpYIDzPykX5u2esqZ6Pnu99hdoXEpYM8pl237O%2FuNwpzVIfWRLArXaol3qtXkK%2FDqai97z9MMB2Tu23MLRT5iGNONJVWAyHg7%2F2NI7fUhsI0wOE8e8%3D&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Date=20210705T132631Z&X-Amz-SignedHeaders=host&X-Amz-Expires=300&X-Amz-Credential=ASIAR5SGMCEDKW3XMSOE%2F20210705%2Fap-northeast-1%2Fs3%2Faws4_request&X-Amz-Signature=ba0c8d89831de2a56de4e9ce3b2c953d657f20580cfbb87410e574ecafec6abf"
    )

</template>

<script>
import axios from 'axios'
import pdf from 'vue-pdf'

export default {
  components: {
    pdf
  },
  data () {
    return {
      test:{},
      blobData: {},
      buildingDocument: false
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
