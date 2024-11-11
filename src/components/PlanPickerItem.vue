<template>
  <div @click="selectedPlan" class="plan">
    <div class="description">
      <span class="title">
        {{ name }} {{ selected ? '🌟': '💥'}}
      </span>
    </div>
  </div>
</template>

<script setup>
  import {ref} from 'vue';
  //usando un macro
  //defenir las props
  //defineProps(['name','planIcon']);
 const props = defineProps({
    name: {
      type: String,
      required: true
    }
  });
  
  //definir eventos
  const emit = defineEmits(['select']);
  //variable que permite recordar si el plan ha sido seleccionado
  const selected = ref(false);
  //funcion que permimte cambiar el valor de la variable
  const selectedPlan = () => {
    selected.value = true;
    //plan ha sido seleciconado
    emit('select', props.name);
  };



</script>

<style scoped>

</style>