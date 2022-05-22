<template>
<h1 class="text-3xl font-bold underline">
    Benefits List!
  </h1>
  <img class="mx-auto" alt="Vue logo" src="./assets/logo.png" />
  <Benefits :benefits="benefitsList" />
</template>

<script>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import Benefits from './components/Benefits.vue'
import { ref } from 'vue';

export default {
  components: {Benefits},
  setup(){
    const benefitsList = ref([
      {id: 1, sectionName: 'Seccion 8', benefitsPlans: ['Muerte accidental', 'cancer', 'perdida ingresos']},
      {id: 2, sectionName: 'Seccion 26', benefitsPlans: ['Muerte Laboral', 'cancer', 'perdida ingresos', 'Perdida de ojo']},
      {id: 3, sectionName: 'Seccion 2', benefitsPlans: ['Muerte Natural', 'Perdida de Organos', 'perdida ingresos']},
      {id: 4, sectionName: 'Seccion 17', benefitsPlans: ['Muerte Vehicular', 'perdida ingresos']},
      {id: 5, sectionName: 'Seccion 90', benefitsPlans: ['Muerte Por abeja', 'Muerte por cigarros', 'Muerte por sobrepeso', 'Muerte por asfixia']},
      {id: 6, sectionName: 'Seccion 26', benefitsPlans: ['Muerte Por trompo', 'Muerte por extravio', 'Muerte por golpes', 'Muerte por ahogo']},
      {id: 7, sectionName: 'Seccion 4', benefitsPlans: ['Muerte Por bala', 'Muerte por atropello', 'Muerte por asalto', 'Muerte por sobrepeso']},
      {id: 8, sectionName: 'Seccion 18', benefitsPlans: ['Muerte Por resbalon', 'Muerte accidental', 'Muerte por sobrepeso', 'Muerte por cancer']},
    ]);


    return {
        benefitsList  
    }
  }
}
</script>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
