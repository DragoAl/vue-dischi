<template>
    <div id="disc-cont">
        <div class="loading" v-if="discsList.length === 0">LOADING...</div>
        <div v-else id="disc-list">
            <Disc 
            v-for ="disc, i in discsList"
            :key="i"
            :details="disc"
        />
        </div>

        
    </div>
</template>

<script>
import axios from "axios";
import Disc from '../components/Disc.vue'

export default ({
    name: 'ListDisc',
    components: {
        Disc
    }, 

    data() {
        return {
           discsList : [], 
        }
    },

    created() {
        this.getDisc();
    },

    methods: {
        getDisc() {
            axios
            .get("https://flynn.boolean.careers/exercises/api/array/music")
            .then((result) =>{
                this.discsList = result.data.response;
            })
        }
    }
})
</script>

<style scoped lang="scss">
    #disc-cont {
        background-color:#1e2d3b ;
        width: 70%;
        margin: 50px auto 0 ;
        
        #disc-list{
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
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
