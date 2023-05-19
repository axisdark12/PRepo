<script setup>
import {onMounted, ref} from "vue";

//import BlackButton from "./components/BlackButtton.vue";
import BlogPost from "./components/BlogPost.vue";
import PaginacionPost from "./components/PaginacionPost.vue";
import CircleLoading from "./components/CircleLoading.vue"

const post = ref ([]);
const postXpage =5;
const inicio = ref (0);
const fin = ref (postXpage);
const fav = ref();
const loading = ref(true);
const cambiarFavorito = (title) => {
    fav.value = title
}

// Esta version deberia funcionar con el metodo que se creo abajo de fetch data 
//  loading.value=true;
//Carga despues de sus componentes
// onMounted(async() => {
    
// try {
//     const res = await fetch('https://jsonplaceholder.typicode.com/posts')
//     post.value = await res.json();
// } catch (error) {
//     console.log(error)
// }finally{
//     setTimeout(()=>{
//   loading.value=false
//  },2000)
// }
// })

//version que carga al mismo tiempo
// fetch('https://jsonplaceholder.typicode.com/posts')
// .then(res => res.json())
// .then(data => {
// post.value = data;
// })
// .finally(()=> {
//     setTimeout(()=>{
//         loading.value=false
//     },1000)
// })

const fetchData = async () =>{
    try {
        const res = await fetch('https://jsonplaceholder.typicode.com/posts')
        post.value = await res.json();
    } catch (error) {
        console.log(error)
    }finally{
        setTimeout(()=>{
      loading.value=false
     },2000)
    }    
}
fetchData ();


const next = () => {
    //normal
    inicio.value = inicio.value + postXpage;
    fin.value = fin.value + postXpage;  
}
const prev = () => {
    //acortado
    inicio.value +=- postXpage;
    fin.value +=- postXpage;
}



</script>

<template>
 <CircleLoading v-if="loading"/>
    <div class="container" v-else ="loading">
       
<h1>APP</h1>
<h5>Mi post Favorito es: {{ fav }}</h5>



<PaginacionPost @next="next" @prev="prev" :longitud ="post.length" :inicio="inicio" :fin="fin" class="mb-2"/>

<BlogPost  v-for="post in post.slice(inicio,fin,)" 
:key="post.id" 
:title="post.title" 
:id="post.id"
:body="post.body" 

@cambiarFavorito="cambiarFavorito" />

</div>
</template>



<style>

</style>