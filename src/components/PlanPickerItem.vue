<template>
  <div @click="selectedPlan" class="plan">
    <div class="description">
      <span class="title">
        {{ name }} {{ isSelected ? '🌟': ''}}
      </span>
    </div>
  </div>
</template>

<script setup>
  //importamos la funcion para la propiedad computada
  import { computed } from 'vue';
  //usando un macro
  //defenir las props
  //defineProps(['name','planIcon']);
 const props = defineProps({
    name: {
      type: String,
      required: true
    },
    selectPlan: String
    
  });
  
  //definir eventos
  const emit = defineEmits(['select']);
  //funcion que permimte cambiar el valor de la variable
  const selectedPlan = () => {
    //plan ha sido seleciconado
    emit('select', props.name);
  };

  //creando una propiedad computada para 
  //saber si el plan ha sido seleccionado
  const isSelected = computed(() => {
    return props.name === props.selectPlan;
  });


</script>

<style scoped>

</style>