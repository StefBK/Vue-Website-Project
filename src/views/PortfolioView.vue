<script setup>

import {ref} from 'vue';

const portfolio=ref(null);

let page=1;

const nextPage=()=>{
  page++;
  console.log('page:',page);
  loadPic(page);
}

const loadPic=(page=1)=>{
  // fetch('https://picsum.photos/v2/list?page=1&limit=10')
  fetch('https://picsum.photos/v2/list?page='+page+'&limit=6')
  .then((res)=>res.json())
  .then((json)=>{
    portfolio.value=json;
    console.log(json);
  });
}
// Entre parenthèses pour invocation immédiate de la fonction : exécuter la fonction dès que le script est exécuté sinon sur un événement, sans parenthèses : loadPic()
// (function())() = Définition + Exécution immédiate de la fonction 
(loadPic)()

</script>

<template>
  <button @click="nextPage">Next Page</button>
  <div class="container-fluid">
    <div class="row">
      <div class="col-12">
        <h1>Portfolio</h1>
      </div>
    </div>

    <div class="row">
      <div v-for="pic in portfolio" class="col-12 col-md-4">
        <!-- <div class="card" style="width: 18rem;"> -->
        <div class="card">
          <img v-bind:src="'https://picsum.photos/id/'+pic.id+'/320/240'" class="card-img-top" alt="Card image cap">
          <div class="card-body">
            <h5 class="card-title">{{pic.author}}</h5>
            <p class="card-text">{{pic.url}}</p>
            <a v-bind:href="pic.url" targt="_blank" class="btn btn-primary">Go somewhere</a>
          </div>
        </div>
      </div>
      <!-- {{pic.title}}
      {{pic.description}}
      <img v-bind:src="pic.url" alt=""> -->
    </div>
  </div>
</template>

<style>
/* @media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
} */
</style>
