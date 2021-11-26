<template>
    <div id="disc-cont">
        <Disc 
            v-for ="disc, i in discsList"
            :key="i"
            :details="disc"
        />
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
        width: 80%;
        margin: 0 auto;
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;
    }


</style>
