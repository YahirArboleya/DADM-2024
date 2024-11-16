<script setup>
    import PlanPickerItem from './PlanPickerItem.vue';
    import { ref } from 'vue';

    //creando una referencia reactiva para almacenar el plan seleccionado
    const selectedPlan = ref(null);


    const plans = ref(['El Cafetero', 'El Chelero', 'El Choro']);

    const selectPlan = (name) =>{
      selectedPlan.value = name;
    };

</script>

<template>
    <div class="plans">
      <PlanPickerItem  
      v-for = "plan in plans" 
      :key="plan" 
      :name="plan"
      @select="selectPlan"
      :selectPlan="selectedPlan"/>
    </div>
    <p>{{selectedPlan}}</p>
</template>


<style scoped>

</style>