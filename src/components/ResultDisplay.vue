<template>
    <div class="alert alert-primary" v-if="result !== null">
      Résultat: {{ result }}
    </div>
    <div class="alert alert-danger" v-if="error !== null">
      Erreur: {{ error }}
    </div>
  </template>
  
  <script>
  export default {
    name: 'ResultDisplay',
    props: ['result', 'error']
  }
  </script>
  