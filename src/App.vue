<template>
  <div class="everything">
    <div id="app" class="wrapper">
      <div class="header">
        <h1>Word Translator</h1>
        <h5>Powered by the awesome Vue.js</h5>
      </div>
      <TranslateForm class="form" v-on:formSubmit="translateText"></TranslateForm>
      <TranslateOutput class="output" v-text="translatedText"></TranslateOutput>
    </div>
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
  data(){
    return{
      translatedText: ''
    }
  },
  methods:{
    translateText: function(text, lang){
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key='API_KEY'&lang=' + lang + '&text=' + text)
      .then(response => {
        this.translatedText = response.body.text[0];
      })
    }
  }
}
</script>

<style>
body{
  background: #fefefe;
}

.everything{
  display: flex;
  justify-content: center;
}

.wrapper{
  display: grid;
  grid-gap: 3px;
  padding-top: 20px;
  grid-template-columns: repeat(10, 1fr);
  grid-template-rows: 100px 100px 100px;
  grid-template-areas: 
  "h h h h h h h h h h"
  "f f f f f f f f f f"
  "o o o o o o o o o o"
  ;
}

.header{
  grid-area: h;
}

.form{
  grid-area: f;
}

.output{
  grid-area: o;
}
</style>
