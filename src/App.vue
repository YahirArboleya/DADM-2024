<script setup>
import { ref, computed } from "vue";

const header = ref("Shopping List App");

// Lista de items con prioridad y estado de compra
const items = ref([
  { id: 1, label: "10 bolillos", purchased: false, priority: true },
  { id: 2, label: "1 lata de frijoles", purchased: true, priority: true },
  { id: 3, label: "2 lata de atún", purchased: true, priority: true },
  { id: 4, label: "1/2 lata de pan", purchased: false, priority: false },
  { id: 5, label: "1/4 lata de pan", purchased: false, priority: true },
]);

// Variables del formulario para el nuevo item
const newItem = ref("");
const newItemHighPriority = ref(false);
const editing = ref(false);

// Guardar un nuevo item en la lista
const saveItem = () => {
  if (newItem.value.trim()) {
    items.value.push({
      id: items.value.length + 1,
      label: newItem.value,
      priority: newItemHighPriority.value,
      purchased: false,
    });
    newItem.value = ""; // Limpiar el campo después de guardar
    newItemHighPriority.value = false;
    editing.value = false; // Cerrar el formulario después de guardar
  }
};

// Alternar el estado de edición para abrir/cerrar el formulario
const toggleEditing = () => {
  editing.value = !editing.value;
  if (!editing.value) {
    newItem.value = ""; // Limpiar campos cuando se cierra el formulario
    newItemHighPriority.value = false;
  }
};

// Alternar el estado de "comprado" de un item
const togglePurchased = (item) => {
  item.purchased = !item.purchased;
};

const characterCount = computed(()=>{
  // Toda propiedad computada debe regresar un valor
  return newItem.value.length;
});

</script>

<template>
  <div class="header">
    <h1>
      <i class="material-icons shopping-cart-icon">local_mall</i>
      {{ header }}
    </h1>
    <button v-if="editing" class="btn" @click="toggleEditing">Cancelar</button>
    <button v-else class="btn btn-primary" @click="toggleEditing">Agregar Artículo</button>
  </div>

  <!-- Formulario para añadir items -->
  <form v-if="editing" @submit.prevent="saveItem" class="add-item form">
    <input v-model="newItem" type="text" placeholder="Add Item" />
    <label>
      <input type="checkbox" v-model="newItemHighPriority" />
      High Priority
    </label>
    <button :disabled="newItem.length === 0" class="btn btn-primary">
      Save Item
    </button>
    	<!-- Contador -->
  <p class="counter">
    {{ characterCount }} / 200
  </p>
  </form>

  <!-- Lista de items -->
  <ul>
    <li
      v-for="item in items"
      :key="item.id"
      @click="togglePurchased(item)"
      :class="{ strikeout: item.purchased, priority: item.priority }"
    >
      ⚜ {{ item.label }}
    </li>
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
