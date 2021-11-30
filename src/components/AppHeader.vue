<template>
    <header> 
        <img src="@/assets/spotify.png" alt="">
        <form action="">
            <div>
                <label id="etichetta">SELEZIONA IL TUO GENERE PREFERITO</label>
                <select name="genre" class="selezione" @change="$emit('GenreSelect', $event.target.value )">
                    <option :value="'all'">All</option>
                    <option v-for="option, i in filteredTypes" :key="i">
                        {{option}}
                    </option>
                </select>

            </div>
        
            <div>
                <label id="etichetta">SELEZIONA IL TUO ARTISTA PREFERITO</label>
                <select name="artists" class="selezione" @change="$emit('ArtistSelect', $event.target.value )">
                    <option :value="'all'">All</option>
                    <option v-for="artist, i in filteredArtist" :key="i">
                        {{artist}}
                    </option>
                </select>
            </div>

        </form>

        

    </header>
</template>

<script>
export default {
    name:'AppHeader',
    props : {
        filteredTypes: Array,
        filteredArtist: Array
    }
}
</script>

<style scoped lang="scss">
    header {
        display: flex;
        height: 80px;
        background-color: #2e3a46;
        justify-content: space-between;
        
        
        img {
            width: 50px;
            height: 50px;
            margin: 20px;
        }
    }

    form {
        display: flex;

    }

    .selezione {
        width: 180px;
        height: 35px;
        font-size: 16px;
        border-radius: 15px;
        background-color: #4caf50;
        border: 1px solid black;
        text-align: center;
        margin-left: 70px;
        display: inline-block;

    }
    #etichetta {
        display: block;
        color: white;
        margin: 10px 10px 5px;
    }

</style>