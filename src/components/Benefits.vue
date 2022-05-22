<template>
  <button
    class="bg-emerald-500 p-3 m-2 rounded text-white removeActive shadow-md hover:shadow-cyan-500"
    @click="changeBenefitSection(benefit.id)"
    v-for="benefit in benefits"
    :key="benefit.id"
    :id="benefit.id"
  >
    {{ benefit.sectionName }}
  </button>
  <div class="container overflow-hidden">
    <TransitionGroup
      :duration="{ enter: 1000, leave: 2002 }"
      name="fade"
      enter-active-class="animate__animated animate__lightSpeedInLeft"
      leave-active-class="animate__animated animate__lightSpeedOutRight"
      tag="ul"
      @BeforeLeave="endAnimation"
    >
        <li  v-for="(benefitPlan, index) in benefitsPlans" :key="benefitPlan">
              <p>{{Number(index) + 1}}: {{ benefitPlan }}</p>
        </li>
    </TransitionGroup>
  </div>
</template>

<script>
import { ref, onMounted } from "vue";
export default {
  props: {
    benefits: Array,
  },
  setup(props) {
    const benefits = ref(props.benefits);
    const benefitsPlans = ref([]);
    const buttonsSection = ref(null)
    const randomActiveSelection = Math.floor(Math.random() * 4)

    /* Al cargar el component */
    onMounted(() => {
      buttonsSection.value = document.querySelectorAll('.removeActive');
      buttonsSection.value[randomActiveSelection].classList.add('bg-cyan-500', 'shadow-cyan-500')
      benefitsPlans.value = { ...benefits.value[randomActiveSelection].benefitsPlans};
    });

    const endAnimation = () => {
      console.log("Animacion finalizada")
    }

    /* Al hacer click en los botones */
    const changeBenefitSection = (idx) => {
      benefitsPlans.value = { ...benefits.value[idx - 1].benefitsPlans};
      buttonsSection.value.forEach(ele => {
        /* Eliminamos las classes active de todos los botonos */
        ele.classList.remove('bg-cyan-500', 'shadow-cyan-500')
      })
      /* Agregamos clases para hacer saber que el boton esta activo */
      buttonsSection.value[idx - 1].classList.add('bg-cyan-500', 'shadow-cyan-500')
    };
    
    return {
      benefits,
      benefitsPlans,
      endAnimation,
      changeBenefitSection,
    };
  },
};
</script>



