<script setup>

import BlackButton from "./components/BlackButtton.vue";
import BlogPost from "./components/BlogPost.vue";
import {ref} from "vue";
const post = ref ([
    {title: 'post 1',id: 1,body: 'Descripcion 1'},
    {title: 'post 2',id: 2,body: 'Descripcion 2'},
    {title: 'post 3',id: 3,body: 'Descripcion 3'},
    {title: 'post 1',id: 1},
    
]);

const fav = ref('');

const cambiarFavorito = (title) => {
    fav.value = title
  
}



</script>

<template>


<h1>APP</h1>
<h5>Mi post Favorito es: {{ fav }}</h5>

<BlogPost  v-for="post in post" 
:key="post.id" 
:title="post.id" 
:body="post.body" 
:cambiarFavorito="cambiarFavorito" />
</template>



<style>

</style>