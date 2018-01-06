<template>
    <div id="translateForm">
        <form class="contain" id="translateForm" v-on:submit="formSubmit">
            <input class="form-control translate" type="text" placeholder="Enter word to translate" v-model="textToTranslate">
            <select class="form-control lang" v-model="language">
                <option value="hi">Hindi</option>
                <option value="de">German</option>
                <option value="es">Spanish</option>
                <option value="ja">Japanese</option>
                <option value="fr">French</option>
            </select>

            <input class="btn btn-primary submitBtn" type="submit" value="Translate">
        </form>
    </div>
</template>

<script>
export default {
  name: 'translateForm',
  data(){
      return{
          textToTranslate: '',
          language: ''
      }
  },
  created(){
      this.language = 'hi';
  },
  methods: {
      formSubmit(e){
          this.$emit('formSubmit', this.textToTranslate, this.language);
          e.preventDefault();
      }
  }
}
</script>
<style>
  .contain{
      display: grid;
      grid-gap: 15px;
      grid-template-columns: repeat(6, 1fr);
      grid-template-rows: 40px 40px;
      grid-template-areas:
        "t t t l l l"
        ". . s s . ."
      ;
  } 

  .translate{
      grid-area: t;
  } 

  .lang{
      grid-area: l;
  }

  .submitBtn{
      grid-area: s;
  }
</style>
