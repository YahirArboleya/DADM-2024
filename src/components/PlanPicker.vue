<script setup>
    import PlanPickerItem from './PlanPickerItem.vue';
    import { ref, onMounted } from 'vue';


    //creando una referencia reactiva para almacenar el plan seleccionado
    const selectedPlan = ref(null);


    const plans = ref(['El Cafetero', 'El Chelero', 'El Choro']);

    const selectPlan = (name) =>{
      selectedPlan.value = name;
    };

    const plansWrapper = ref(null);

    //intentando obtener la referencia al elemento .plans
    console.log("Termina de ejecutar el script setup");

    //registrando el took mounted
    //tooks: funciones que se ejecutan cuando el ciclo de vida de un componenete cambia
    onMounted(()=>{
      console.log("El componente PlanPicker se ha montado")
      console.log(plansWrapper.value);
    });
</script>

<template>
    <div ref="plansWrapper" class="plans">
      <PlanPickerItem  
      v-for = "plan in plans" 
      :key="plan" 
      :name="plan"
      @select="selectPlan"
      :selectPlan="selectedPlan"/>
    </div>
</template>


<style scoped>

</style>