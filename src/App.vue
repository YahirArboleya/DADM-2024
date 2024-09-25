<script setup>
  import {ref} from 'vue';
  //Modelo
  const header = ref('App lista de compras');
  const items = ref([
    {id: '0', label:'10 Bolillos'},
    {id: '1', label:'1 Lata de frijoles'},
    {id: '2', label:'1 Chelas'},
    {id: '3', label:'1 Nutella'}
  ]);

  const newItem = ref('');
  const newItemPriority = ref('low');

</script>

<template>
  <h1>
    <i class="material-icons shopping-cart-icon">local_mall</i>
    {{ header }} 
  </h1>

  <input v-model="newItem" type="text" placeholder="Agregar Artículo">

  <!--Ratio buttons-->
  <label><input type="radio" value="low" v-model="newItemPriority">Baja</label>
  <label><input type="radio" value="hight" v-model="newItemPriority">Alta</label>
  {{ newItemPriority == 'low'? '❤️':'⭐'  }}

  <ul>
    <li v-for="item in items" v-bind:key="item.id">  🛒 {{ item.label }} </li>
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
