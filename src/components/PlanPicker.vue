<script setup>
    import PlanItem from './PlanPickerItem.vue';
    import { ref } from 'vue';
    const plans = ref(['El Cafetero', 'El Chelero', 'El Choro']);
</script>

<template>
    <div class="plans">
      <PlanItem  v-for = "plan in plans" :key="plan" :name="plan"></PlanItem>    
    </div>
</template>


<style scoped>

</style>