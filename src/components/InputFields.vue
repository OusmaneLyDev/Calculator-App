<template>
    <div class="mb-3">
      <div v-if="showFields">
        <input type="number" class="form-control mb-2" v-model.number="value1" placeholder="Entrez la première valeur">
        <input type="number" class="form-control" v-model.number="value2" placeholder="Entrez la deuxième valeur">
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'InputFields',
    props: ['showFields'],
    data() {
      return {
        value1: null,
        value2: null
      }
    },
    watch: {
      value1(val) {
        this.$emit('input-changed', { value1: val, value2: this.value2 });
      },
      value2(val) {
        this.$emit('input-changed', { value1: this.value1, value2: val });
      }
    }
  }
  </script>
  