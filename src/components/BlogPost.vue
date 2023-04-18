<script setup>


defineProps(['title','colorText'])
</script>

<template>
<div class="card">
    <div class="card-body">
        
        <h5 class="card-tittle" :class="`text-${colorText}`" > {{title}}  </h5>
      <p> Lorem ipsum dolor sit amet. </p>
        
    </div>
</div>

</template>