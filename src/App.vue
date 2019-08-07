<template>
  <div class="text-center" id="app">
    <h1>Word Translator</h1>
    <h5>Powered By Vue.js and Yandex Translate API</h5>
    <TranslateForm v-on:formSubmit="translateText"></TranslateForm>
    <TranslateOutput v-text="translatedText"></TranslateOutput>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm';
import TranslateOutput from './components/TranslateOutput';

export default {
  name: 'App',
  components: {
    TranslateForm,
    TranslateOutput
  },
  data: function(){
return {
  translatedText:''
}
  },
  methods: {
    translateText:function(text, language){
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20190807T184624Z.fdfcb14985197f5c.006889dbad439f9a4f51a6ff6ece05062dd05893&lang='+language+'&text='+text)
      .then((response) => {
         this.translatedText = response.body.text[0];
      });
    }
  }
}
</script>

<style>
</style>
