<template>
  <div class="plan">
    <div class="description">
      <span class="title">
        {{ name }}
      </span>
    </div>
  </div>
</template>

<script setup>
  //usando un macro
  //defenir las props
  //defineProps(['name','planIcon']);
  defineProps({
    name: {
      type: String,
      required: true
    }
  })


</script>

<style scoped>

</style>