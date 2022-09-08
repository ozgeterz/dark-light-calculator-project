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
  @import url('https://fonts.googleapis.com/css?family=Poppins:400,700,900');
#app {
font-family: 'Poppins';
font-style: normal;
font-weight: 600;

}
</style>
