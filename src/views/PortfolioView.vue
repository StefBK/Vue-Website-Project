<script setup>
// const msg="Hello les Amis !"
// let portfolio=[
//   {title:'First Picture', description:'Ben première Image...'},
//   {title:'Second Picture', description:'Ben deuxième Image...'}
// ]
import {ref} from 'vue';
const portfolio=ref(null);
// fetch('https://picsum.photos/v2/list?page=1&limit=10')
fetch('http://127.0.0.1:8000/api/picture?page=1&limit=6')
.then((res)=>res.json())
.then((json)=>{
  portfolio.value=json;
  console.log(json);
})
</script>

<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-12">
        <!-- <h1>Portfolio{{msg}}</h1> -->
        <h1>Portfolio</h1>
      </div>
    </div>

    <div class="row">
      <div v-for="pic in portfolio" class="col-12 col-md-4">
        <!-- <div class="card" style="width: 18rem;"> -->
        <div class="card">
          <img v-bind:src="pic.url" class="card-img-top" alt="Card image cap">
          <div class="card-body">
            <h5 class="card-title">{{pic.title}}</h5>
            <p class="card-text">{{pic.description}}</p>
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
