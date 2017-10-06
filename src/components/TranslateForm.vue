<template>
  <div class="row" id="translateForm">
    <div class="col-md-4 col-md-offset-4">
      <form class="well" v-on:submit="formSubmit">
        <input class="form-control" type="text" v-model="textToTranslate" placeholder="Enter a Word">
        <select class="form-control" v-model="language">
          <option value="ru">Russian</option>
          <option value="es">Spanish</option>
          <option value="fr">French</option>
          <option value="zh">Chinese</option>
        </select>
        <br>
        <input class="btn btn-lg btn-default" type="submit" value="Translate">
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TranslateForm',
  data () {
    return {
      textToTranslate: '',
      language: ''
    }
  },
  created () {
    this.language = 'ru'
  },
  methods: {
    formSubmit (e) {
      this.$emit('formSubmit', this.textToTranslate, this.language)
      e.preventDefault()
    }
  }
}
</script>

<style>

</style>

