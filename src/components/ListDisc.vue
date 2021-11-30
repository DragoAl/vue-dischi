<template>
    <div id="disc-cont">
        <!-- passo nelle props l'array con i generi filtrati -->
        <!-- richiamo l'eventi passato da emit e gli passo il metodo che setta il genere in base a quello filtrato -->
        <!-- <SelectType
            :GenList="filteredTypes"
            @GenreSelect ='SelectedGenre'
        /> -->
        
       
        <div class="loading" v-if="discsList.length === 0">LOADING...</div>
        <div v-else id="disc-list">
            <Disc 
            v-for ="disc, i in filteredListDisk"
            :key="i"
            :details="disc"
        />
        </div>

        
    </div>
</template>

<script>
import axios from "axios";
import Disc from '../components/Disc.vue'
// import SelectType from'../components/SelectType.vue'


export default ({
    name: 'ListDisc',
    components: {
        Disc,
        // SelectType
    }, 

    data() {
        return {
           discsList : [],
           filteredTypes : [],
        //    selectOpt : "all"
        }
    },
    props : {
        selectOpt: String
    },

    created() {
        this.getDisc();
    },

    computed:{
        // creo un array per filtrare i generi
        filteredListDisk(){
            if(this.selectOpt === "all"){
                return this.discsList
            }
            return this.discsList.filter((item) => {
                return item.genre.toLowerCase().includes(this.selectOpt.toLowerCase())
            })
        },
    },

    methods: {
        getDisc() {
            axios
            .get("https://flynn.boolean.careers/exercises/api/array/music")
            .then((result) =>{
                this.discsList = result.data.response;
                
                // passo la lista dei generi con emit, che serve al select
                this.filteredTypeToSelect();
                console.log(this.discsList);
            })
        },
        // filtro l'array per avere elementi univoci
        filteredTypeToSelect() {
            for (let i =0; i< this.discsList.length; i++ ) {
                if (!this.filteredTypes.includes(this.discsList[i].genre)){
                    this.filteredTypes.push(this.discsList[i].genre)
                }
            }
            // console.log(this.filteredTypes);
            // return this.filteredTypes
            this.$emit('genreReady',this.filteredTypes)
        },
        // riprende il valore dall'array filtrato e lo mette uguale al valore passato dal select
        // SelectedGenre(genere) {
        //     this.selectOpt = genere;
        // }
    }
})
</script>

<style scoped lang="scss">
    #disc-cont {
        background-color:#1e2d3b ;
        width: 70%;
        margin: 50px auto  ;
        
        #disc-list{
            display: flex;
            flex-wrap: wrap;
            justify-content: space-around;
            margin-bottom: 50px;
        }
    }
    .loading {
        text-align: center;
        font-size: 30px;
        font-weight: bold;
        color: black;
    }


</style>
