<template>
  <div class="d-flex justify-content-center">
        <form id="transForm" class="" v-on:submit="formSubmit">
            <input class="form-control" type="text" v-model="textToTranslate" placeholder="Enter text here!">
            <select class="form-control" v-model="language">
                <option value="ru">Russian</option>
                <option value="es">Spanish</option>
                <option value="fr">French</option>
                <option value="zh">Chinese</option>
                <option value="az">Azerbaijan</option>
                <option value="de">German</option>
            </select>
            <input class="btn btn-primary" type="submit" value="Translate">
        </form>
  </div>
</template>

<script>

export default {
    name: 'translateForm',
    data() {
        return {
            textToTranslate:'',
            language:''
        }
    },
    created(){
        this.language = 'ru';
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
  #transForm{
      border-radius: 10px;
      border: 1px #ccc solid;
      align-content: center;
      padding: 10px;
      min-width: 25em;
  }
</style>
