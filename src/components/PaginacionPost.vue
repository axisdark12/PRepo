<script setup>
const emit = defineEmits(['next','prev']);
defineProps(["inicio","fin","longitud"]);
</script>

<template>




<div class="btn-group " role="group" aria-label="Basic example">
  <button  :disabled="inicio <= 0" @click ="emit('prev')" type="button" class="btn btn-outline-secondary">Anterior {{ inicio }}</button>
  <button  :disabled="fin >=longitud" @click ="emit('next')" type="button" class="btn btn-outline-secondary">Siguiente {{ fin }}</button>
</div>


</template>