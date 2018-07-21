<template>
  <div id="app" class="text-center">
    <h1>Vue Translate</h1>
    <h5>Powered by the Yandex API.</h5>
    <TranslateForm v-on:formSubmit="translateText"></TranslateForm>
    <TranslateOutput v-text="translatedText"></TranslateOutput>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'

export default {
  name: 'App',
  components: {
    TranslateForm,
    TranslateOutput
  },
  data: function() {
    return {
      translatedText:''
    }
  },
  methods: {
    translateText: function(text, language) {
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180721T143035Z.e008d0e677b649f9.550ce9d8cded8fa573043b5d24cba333e4c98b95&lang=' + language + '&text=' + text)
      .then(response => {
        this.translatedText = response.body.text[0];
      });
    }
  }
}
</script>

<style>

#app {
  color: black;
}

body {
  margin-top: 40px;
  font-family: 'Avenir';
  background: #2d2d2d;
}

@font-face {
  font-family: Avenir;
  src: url(https://www.wfonts.com/download/data/2016/06/21/avenir/AEH.ttf);
}
</style>
