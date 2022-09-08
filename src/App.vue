<template>
  <div id="app">
   <calculator-component/>
  </div>
</template>

<script>
import CalculatorComponent from './components/CalculatorComponent.vue'


export default {
  name: 'App',
  components: {
    CalculatorComponent,
  }
}
</script>

<style>
#app {
 
font-family: 'Poppins';
font-style: normal;
font-weight: 600;

}
</style>
