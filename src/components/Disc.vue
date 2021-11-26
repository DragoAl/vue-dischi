<template>
<div id="disc">
    <img :src="details.poster" :alt="details.title">
    <h2>{{details.title}}</h2>
    <span>{{details.author}}</span>
    <span>{{details.year}}</span>
</div>
    
</template>

<script>
export default {
    name:'Disc',
    props : {
        details: Object,
    }
}
</script>

<style scoped lang="scss">
    #disc {
       width: 20%; 

       img {
            max-width: 100%;
        }
    }

</style>