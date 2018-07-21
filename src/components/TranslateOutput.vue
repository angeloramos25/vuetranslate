<template>
  <h3>{{translatedText}}</h3>
</template>

<script>

export default {
  name: 'translateOutput',
  props: [
    'translatedText'
  ]
}
</script>

<style>

h3 {
  padding-top: 30px;
}

</style>
