<script setup>
    import PlanPickerItem from './PlanPickerItem.vue';
    import { ref } from 'vue';
    const plans = ref(['El Cafetero', 'El Chelero', 'El Choro']);

    const selectedPlan = (name) =>{
      console.log(name)
    }
</script>

<template>
    <div class="plans">
      <PlanPickerItem  
      v-for = "plan in plans" 
      :key="plan" 
      :name="plan"
      @select="selectedPlan"/>
    </div>
</template>


<style scoped>

</style>