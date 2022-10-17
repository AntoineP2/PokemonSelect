<template>
  <div class="containt-show-stat" v-if="name != null">
    <p>NOM : {{ name }}</p>
    <p>TYPE 1 : {{ type1 }}</p>
    <p v-if="type2 != null">TYPE 2 : {{ type2 }}</p>
  </div>
</template>

<script>
export default {
    name:"DisplayStat",
    props:{
        name : String,
        type1 : String,
        type2: String,

    }
}
</script>

<style>
    .containt-show-stat{
        border: 1px solid white;
        padding : 0px 20px;
        background-color: #9d4edd;
        width : 250px;

    }
    p{
        font-size: 25px;
        font-weight: bold;
    }
</style>