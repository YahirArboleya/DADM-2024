<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import { ref } from "vue";

const header = ref("🛒 Shopping List App");
const items = ref([
  { id: 1, label: "10 bolillos" },
  { id: 2, label: "1 lata de frijoles" },
  { id: 3, label: "2 lata de atún" },
]);
const newItem = ref("");
const newItemHighPriority = ref(false);
</script>

<template>
  <h1>{{ header }}</h1>
  <input v-model.trim="newItem" type="text" placeholder="Add Item" />
  <!-- Caja de seleccion de prioridad -->
  <label>
    <input type="checkbox" v-model="newItemHighPriority">
    High Priority
  </label>
  <!-- Lista -->
  <ul>
    <li v-for="({ id, label }, index) in items" key="id">⚜ {{ label }}</li>
  </ul>
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
