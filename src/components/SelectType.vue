<template>
<form action="">
    <label id="etichetta">SELEZIONA IL TUO GENERE PREFERITO</label>
    <select name="genre" id="selezione" @change="$emit('GenreSelect', $event.target.value )">
        <option :value="'all'">All</option>
        <option v-for="option, i in GenList" :key="i">
            {{option}}
        </option>
    </select>
</form>
   
</template>

<script>
export default {
    name:'SelectType',
    props : {
        GenList: Array
    }


}
</script>

<style scoped lang="scss">
#selezione {
    width: 180px;
    height: 50px;
    font-size: 22px;
    border-radius: 20px;
    background-color: #4caf50;
    border: 1px solid black;
    text-align: center;

}
#etichetta {
    display: block;
    color: white;
    margin-bottom: 10px;
}

</style>