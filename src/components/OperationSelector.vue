<template>
    <div class="mb-3">
      <h3>Choisissez une opération</h3>
      <div class="form-check">
        <input class="form-check-input" type="radio" id="addition" value="addition" v-model="selectedOperation">
        <label class="form-check-label" for="addition">Addition</label>
      </div>
      <div class="form-check">
        <input class="form-check-input" type="radio" id="subtraction" value="subtraction" v-model="selectedOperation">
        <label class="form-check-label" for="subtraction">Soustraction</label>
      </div>
      <div class="form-check">
        <input class="form-check-input" type="radio" id="multiplication" value="multiplication" v-model="selectedOperation">
        <label class="form-check-label" for="multiplication">Multiplication</label>
      </div>
      <div class="form-check">
        <input class="form-check-input" type="radio" id="division" value="division" v-model="selectedOperation">
        <label class="form-check-label" for="division">Division</label>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'OperationSelector',
    data() {
      return {
        selectedOperation: ''
      }
    },
    watch: {
      selectedOperation(newVal) {
        this.$emit('operation-selected', newVal);
      }
    }
  }
  </script>
  