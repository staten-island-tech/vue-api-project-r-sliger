<template>
  <div>
    <h1 class="h1">Find the date every Rick And Morty Episode came out.</h1>
      <ul class= "episode-table">
        <li 
        class="episode-list-item" 
        v-for="episode in episodes" 
        :key="episode.name"
        >
        <Eppreview :episode="episode" />
        </li>
      </ul>   
  </div>
</template>

<script>
import Eppreview from "./Eppreview.vue"
export default {
    name: "Eplist",
    data(){
        return{episodes: [],
        epid: null,};
    },
    created: function () {
        this.fetchData();
    },
    methods:{
        fetchData: async function(){
            try {
                const result = await fetch(
                    `https://rickandmortyapi.com/api/episode`
                );
                const data = await result.json();
                this.episodes = data.results;
            } catch (error) {
                alert(error);
            }
        }
    },
    components: { Eppreview },
};

</script>

<style>
html,
body,
* {
  font-size: 62.5%;
  margin: 0;
  padding: 0;
  color: white;
  box-sizing: border-box;
}
html {
  background-color: #111;
}
.home {
  background-color: #111;
}
.link,
.link:visited,
.link:link {
  color: #fff;
  text-decoration: none;
}
.back-link {
  font-size: 3rem;
  text-transform: uppercase;
}
.episode-table {
  display: flex;
  flex-wrap: wrap;
  width: 80vw;
  margin: 0 auto;
  justify-content: space-between;
}
.episode-list-item {
  width: 25rem;
  color: white;

  list-style: none;
  margin: 2.5rem auto;
  transition: all 0.3s;
  padding: 1.5rem;
  font-size: 1.5rem;
  text-transform: uppercase;
}
.episode-list-item img {
  width: 50%;
}
.episode-list-item:hover {
  transform: scale(1.1);
}
.h1{
  font-size: 4rem;
  margin: 4rem;
}
</style>