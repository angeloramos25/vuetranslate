<template>
  <div class="row" id="translateForm">
    <div class="offset-md-3 col-md-6">
      <form v-on:submit="formSubmit">
        <input class="form-control" type="text" v-model="textToTranslate" placeholder="Enter a word or phrase.">
        <select class="form-control" v-model="language">
          <option value="ru">Russian</option>
          <option value="es">Spanish</option>
          <option value="fr">French</option>
          <option value="zh">Chinese</option>
        </select>
        <input class="btn btn-primary" type="submit" value="Translate">
      </form>
    </div>
  </div>
</template>

<script>

export default {
  name: 'translateForm',
  data() {
    return {
      textToTranslate:'',
      language: ''
    }
  },
  created() {
    this.language = 'ru';
  },
  methods: {
    formSubmit(event) {
      this.$emit('formSubmit', this.textToTranslate, this.language);
      event.preventDefault();
    }
  }
}
</script>

<style>

.form-control {
  margin-top: 30px;
}

.btn {
  margin-top: 40px;
}

</style>
