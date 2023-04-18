<script setup>

//defineProps(['title','colorText'])
//Datos que puede utilizar el objeto en vue String, Number Boolean , Array, Object, Date, Function, Symbol

defineProps({
  title: String,
  id:Number,
  colorText:String,
  body:{
    type:String,
    default: 'No hay descripcion de esta wea'
  }
})

const emit = defineEmits(['cambiarFavoritoNombre'])

</script>

<template>
<div class="card">
    <div class="card-body">
        
        <h5 class="card-tittle" :class="`text-${colorText}`" > {{ id }} -> {{title}}  </h5>
      <p> {{ body }} </p>
      <button @click="emit('cambiarFavoritoNombre',title)" 
      class="btn btn-outline-primary" > Favorito</button>
        
    </div>
</div>

</template>