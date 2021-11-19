<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <div class="btn-c" v-for="episode in episodes" v-bind:key="episode.name">
      <button value="1">{{episode.name}}</button>
  </div>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'Home',
  data() {
    return {
      episodes: [{
        name: "Pilot",
      },{
        name: "Lawnmower Dog",
      },{
        name: "Anatomy Park"
      }]
    }
  }
}
fetch('https://rickandmortyapi.com/api/episode')
.then(data => {
return data.json();
})
.then(data => {
console.log(data.results);
});
</script>

<style>
</style>