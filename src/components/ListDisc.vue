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
           //selectOpt : "all"
           filteredArtists: []
        }
    },
    props : {
        // prende la stringa che gli viene passata da AppHeader tramite app
        selectOpt: String,
        selectArtist: String,
    },

    created() {
        this.getDisc();
    },

    computed:{
        // creo un array per filtrare i generi
        filteredListDisk(){
            if(this.selectOpt === "all" && this.selectArtist === "all"){
                return this.discsList
            }

            return this.discsList.filter((item) => {
                if(this.selectOpt !== "all" && this.selectArtist === "all"){
                    return item.genre.toLowerCase().includes(this.selectOpt.toLowerCase())
                }else if (this.selectOpt === "all" && this.selectArtist !== "all"){
                    return item.author.toLowerCase().includes(this.selectArtist.toLowerCase())
                }   
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
                this.filteredArtistToSelect();
            })
        },
        // filtro l'array per avere elementi univoci
        filteredTypeToSelect() {
            for (let i =0; i< this.discsList.length; i++ ) {
                if (!this.filteredTypes.includes(this.discsList[i].genre)){
                    this.filteredTypes.push(this.discsList[i].genre)
                }
            }            
            // $emit comunica l'array filtrato ad app per farlo prendere da AppHeader
            this.$emit('genreReady',this.filteredTypes)
        },
        // riprende il valore dall'array filtrato e lo mette uguale al valore passato dal select
        // SelectedGenre(genere) {
        //     this.selectOpt = genere;
        // }
        filteredArtistToSelect() {
            for (let i =0; i< this.discsList.length; i++ ) {
                if (!this.filteredArtists.includes(this.discsList[i].author)){
                    this.filteredArtists.push(this.discsList[i].author)
                }
            }            
            // $emit comunica l'array filtrato ad app per farlo prendere da AppHeader
            this.$emit('artistReady',this.filteredArtists)
        },
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
