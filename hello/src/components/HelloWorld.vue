<template>
  <div class="hello">
    <h1>
      Rick and Morty Episode Sorter
    </h1>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}

fetch('https://rickandmortyapi.com/api/episode')
.then(data => {
return data.json();
})
.then(data => {
console.log(data);
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
