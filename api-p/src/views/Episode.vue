    <template> 
    <div>
        
        <h1 class="fail"> I Give Up </h1>
    <li class="date">
        {{air_date}}
    </li>
    <h1 class="h1"></h1> 
    </div>
    
    </template>

<script>
export default{
    data() {
        return{
            singleEp: {},
            air_date: [],
        }
    },
    mounted:function(){
        this.fetchData();
    },
    methods: {
       fetchData: async function(){
            try {
                const result = await fetch(
                    `https://rickandmortyapi.com/api/episode/${this.$route.params.id}`
                );
                const singleEP = await result.json();
                this.singleEP = singleEP;
                this.air_date= singleEP.air_date
            } catch (error) {
              console.log(error)  
            }
        },
    }
}   
</script>

<style>
.date{
    font-size: 3rem;
}
.fail{
padding: 2rem;
font-size: 2.9rem;
color: green;
}
</style>