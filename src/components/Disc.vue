<template>
<div id="disc">
    <img :src="details.poster" :alt="details.title">
    <h3>{{details.title}}</h3>
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
       width: calc(100% / 5 - 30px); 
       height: 350px;
       background-color:#2e3a46;
       margin: 15px;
       text-align: center;

       img {
            max-width: 80%;
            padding-top: 20px;
        }
        h3 {
            text-transform: uppercase;
            margin: 5px 10px 20px;
            line-height: 20px;
            color: white;
        }
        span {
            
            color:#6d7675 ;
            display: block;
        }
    }

</style>