<template>
  <div class="container mt-5">
    <OperationSelector @operation-selected="setOperation"/>
    <InputFields :showFields="operation" @input-changed="calculateResult"/>
    <button class="btn btn-primary mt-3" @click="computeResult">Calculer</button>
    <ResultDisplay :result="result" :error="error"/>
  </div>
</template>

<script>
import OperationSelector from './OperationSelector.vue'
import InputFields from './InputFields.vue'
import ResultDisplay from './ResultDisplay.vue'

export default {
  name: 'CalculatorComponent',
  components: {
    OperationSelector,
    InputFields,
    ResultDisplay
  },
  data() {
    return {
      operation: '',
      value1: null,
      value2: null,
      result: null,
      error: null
    }
  },
  methods: {
    setOperation(operation) {
      this.operation = operation;
      this.result = null;
      this.error = null;
    },
    calculateResult(inputs) {
      this.value1 = inputs.value1;
      this.value2 = inputs.value2;
    },
    computeResult() {
      try {
        if (this.operation === '') throw new Error('Aucune opération sélectionnée.');
        if (this.value1 === null || this.value2 === null) throw new Error('Les deux valeurs doivent être fournies.');

        let res;
        switch (this.operation) {
          case 'addition':
            res = this.value1 + this.value2;
            break;
          case 'subtraction':
            res = this.value1 - this.value2;
            break;
          case 'multiplication':
            res = this.value1 * this.value2;
            break;
          case 'division':
            if (this.value2 === 0) throw new Error('Division par zéro impossible.');
            res = this.value1 / this.value2;
            break;
          default:
            throw new Error('Opération inconnue.');
        }
        this.result = res;
        this.error = null;
      } catch (e) {
        this.error = e.message;
        this.result = null;
      }
    }
  }
}
</script>

<style scoped>
/* Ajoutez ici le style pour la calculatrice si nécessaire */
</style>
