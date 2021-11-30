<template>
    <header> 
        <img src="@/assets/spotify.png" alt="">
        <form action="">
            <label id="etichetta">SELEZIONA IL TUO GENERE PREFERITO</label>
            <select name="genre" id="selezione" @change="$emit('GenreSelect', $event.target.value )">
                <option :value="'all'">All</option>
                <option v-for="option, i in filteredTypes" :key="i">
                    {{option}}
                </option>
            </select>
        </form>

    </header>
</template>

<script>
export default {
    name:'AppHeader',
    props : {
        filteredTypes: Array
    }
}
</script>

<style scoped lang="scss">
    header {
        display: flex;
        height: 50px;
        background-color: #2e3a46;
        justify-content: space-between;
        
        
        img {
            width: 40px;
            margin: 5px 15px;
        }
    }
    #selezione {
        width: 180px;
        height: 35px;
        font-size: 16px;
        border-radius: 15px;
        background-color: #4caf50;
        border: 1px solid black;
        text-align: center;

    }
    #etichetta {
        display: block;
        color: white;
        margin-bottom: 5px;
    }

</style>