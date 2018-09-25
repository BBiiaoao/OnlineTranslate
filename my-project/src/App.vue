<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h5 class="text-muted">别查了，反正你也记不住</h5>
    <translate-form v-on:formSubmit="translateText"></translate-form>
    <translate-output :translatedText="translatedText"></translate-output>
  </div>
</template>

<script>
  import TranslateForm from './components/TranslateForm'
  import TranslateOutput from './components/TranslateOutput'

  export default {
    name: 'App',
    data() {
      return {
        translatedText: ""
      }
    },
    components: {
      TranslateForm,
      TranslateOutput
    },
    methods: {
      translateText: function (text, language) {
        console.log(text);
        this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate' +
          '?key=trnsl.1.1.20180916T080453Z.af3d7ba798c0eb53.9dc3ee41ca4acb7af406230ceae6cbcb27329f06' +
          '&lang=' + language +
          '&text=' + text
        ).then((response) => {
          // console.log(response.body.text[0]);
          this.translatedText = response.body.text[0];
        })
      }
    }
  }
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
    /*font-size: 30px;*/
  }
</style>
