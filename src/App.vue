<template>
  <div class="text-center" id="app">
    <h1>Word Translator</h1>
    <h5>Powered by Vue.js</h5>
    <TranslateForm v-on:formSubmit="translateText"></TranslateForm>
    <TranslateOutput v-text="translatedText"></TranslateOutput>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'

export default {
  name: 'app',
  components: {
    TranslateForm,
    TranslateOutput
  },
  data: function () {
    return {
      translatedText: ''
    }
  },
  methods: {
    translateText: function (text, language) {
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20171006T173115Z.ecf6933c4e843186.eed5a042501a23c5b232ebf5021a9a16f017c6fc&lang=' + language + '&text=' + text)
      .then((response) => {
        this.translatedText = response.body.text[0]
      })
    }
  }
}

</script>

<style>
#app {

}
</style>

