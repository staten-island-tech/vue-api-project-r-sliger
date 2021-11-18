<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <h1 class="btn-c">
      <button value="1">episode 1</button>
  </h1>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'Home',
  components: {
    HelloWorld
  }
}
fetch('https://rickandmortyapi.com/api/episode')
.then(data => {
return data.json();
})
.then(data => {
console.log(data.results[0].name);
});
</script>

<style>
</style>