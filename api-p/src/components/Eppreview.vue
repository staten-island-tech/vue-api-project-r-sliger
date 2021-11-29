<template>
  <div>
      <router-link :to="EpisodePath" class="link">
        <div class="ep-container">
            <h1 id="Query">
             {{episode.id}}.
             {{episode.name}}
            </h1>
      </div>
      </router-link>
  </div>
</template>

<script>
export default {
    name: "Eppreview",
    props: ["episode"],
    data() {
        return{
            singeEp: {},
            epid: null,
        };
    },
    mounted: function(){
        this.fetchData();

    },
    methods:{
        fetchData: async function(){
            try {
                const result = await fetch(
                    `https://rickandmortyapi.com/api/episode/${this.episode.id}`
                );
                const singleEP = await result.json();
                this.singleEP = singleEP;
                console.log(this.episode.id)
                 console.log(this.singleEP);
    
            } catch (error) {
              console.log(error)  
            }
        },
    },
    computed: {
        EpisodePath:function(){
            return `/Episode/${this.episode.id}`;
        }
    }
};
</script>

<style>
#query {
  color: #111;
  font-size: 2rem;
}
.ep-container {
  background-color: #999;
  padding: 2rem;
  color: #111;
  font-size: 2.5rem;
}
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
  background-color: green;
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
</style>