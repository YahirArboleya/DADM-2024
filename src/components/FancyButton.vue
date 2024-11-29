<template>
    <button 
      @mouseenter="hover = true"
      @mouseleave="hover = false"> 
      <slot name="icon" :hover="hover">➡️</slot>
      <slot>Submit</slot>
    </button>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  const hover = ref(false);
  </script>

  <style scoped>
  .content{
    text-align: center;
  }
  button{
    width: 12rem;
    margin: 30px auto;
    font-size: 2rem;
  }
  </style>