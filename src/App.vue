<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import { ref } from "vue";
//Modelo
const header = ref("Shopping List App");
// --- items ---
//item model
const items = ref([
  { id: 1, label: "10 bolillos" },
  { id: 2, label: "1 lata de frijoles" },
  { id: 3, label: "2 lata de atún" },
]);

// item method
const saveItem = () =>{
  items.value.push({id: items.value.length + 1, label: newItem.value});
  //Clean the input
  newItem.value = '';
}



//formulario
const newItem = ref('');
const newItemHighPriority = ref(false);
const editing = ref(true);
const activateEdition = (activate) => {
  editing.value = activate;
}

const getLink = () => {
  return newItem.value === '' ? 'https://www.google.com' : 'http://' + newItem.value;
};

const getLinkText = () => {
  return newItem.value === '' ? '💕 Link' : newItem.value;
};

</script>

<template>
<div class="header">
  <h1>
    <i class="material-icons shopping-cart-icon">local_mall</i>
    {{ header }}
    </h1>
    <button v-if="editing" class="btn" @click="activateEdition(false)">Cancelar</button>
    <button v-else class="btn btn-primary" @click="activateEdition(true)">Agregar Artículo</button>
</div>


<!--Colocando un hiperlink-->

<!--
<a :href="getLink()" target="_blank">
    {{ getLinkText() }}
  </a>
-->


  <!-- Formulario -->
  <!-- v-on:submit.prevent para evitar el envío del formulario cuando se presiona Enter-->

<form 
v-on:submit.prevent="saveItem()" 
class="add-item fomr"
v-if="editing">
    <!-- entrada de texto -->
    <input
      v-model.trim="newItem"
      type="text"
      placeholder="Add Item"
    />
    <!-- Caja de seleccion de prioridad -->
    <label>
      <input type="checkbox" v-model="newItemHighPriority" />
      High Priority
    </label>
    <!-- Boton -->
    <button
    :disabled="newItem.length === 0"
    class="btn btn-primary"
    >
      Save Item
    </button>
  </form>

  <!-- Lista -->
  <ul>
    <li v-for="({ id, label }, index) in items" key="id">⚜ {{ label }}</li>
  </ul>

  <p v-if="items.length === 0">🥀 NO HAY ELEMENTOS EN LA LISTA 🥀</p>

</template>

<style scoped>

.shopping-cart-icon{
  font-size: 2rem;

}

header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
