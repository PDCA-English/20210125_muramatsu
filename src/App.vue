<template>
  <div id="app">
      <input type="text" v-model="post_code">
      <button @click="checkPostCode">住所自動入力</button>
      <br>
      <br>
      <div>Address：{{ post_info.allAddress }}</div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      api_key: '6jBX9cqI2JCM7XsTMssELr4P1PrLnkrHQDBiE0v',
      url_base: 'https://apis.postcode-jp.com/api/v2/postcodes/',
      post_code: '',
      post_info: {}
    }
  },
  methods: {
    checkPostCode () {
        fetch(`${this.url_base}${this.post_code}?apiKey=${this.api_key}`)
          .then(res => {
            return res.json();
          }).then(this.setResults);
    },
    setResults (results) {
      this.post_info = results;
    }
  }
}
</script>