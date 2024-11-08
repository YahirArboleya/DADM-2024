<script setup>
    import planItem from './plan-item.vue';
    import { ref } from 'vue';
    const plans = ref(['El Cafetero', 'El Chelero', 'El Choro']);
</script>

<template>
    <div class="plans">
      <planItem  v-for = "plan in plans" :key="plan" :name="plan"></planItem>    
    </div>
</template>


<style scoped>

</style>