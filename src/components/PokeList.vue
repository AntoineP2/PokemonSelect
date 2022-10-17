<template>
  <div class="contain-pokeList"> 
    <div class="pokelist"> <!-- Div pour placer la pokelist au milieu -->
      <div class="button" :key="Pokemon.id" v-for="Pokemon in PokemonList"> <!-- On établis une liste de tout les pokemon -->
        <button
          v-if="!Pokemon.selected || IfSelected"
          :class="Color"
          @click="$emit('choosen-pokemon', Pokemon)"
          @mouseover="$emit('show-stat', Pokemon)" 
          @mouseleave ="$emit('unShow-stat')"
        >
          <img :src="Pokemon.img" />  <!-- Paramètre pour afficher le boutons, si le pokemon est selectionné ou non -->
        </button>
      </div>
    </div>
  </div>
</template>




<script>


import DisplayStat from "./DisplayStat.vue";

export default {
    name: "PokeList",
    props: {
        PokemonList: Object,
        IfSelected: Boolean,
        Color: String,
    },
    component: {
        DisplayStat
    },
    components: { DisplayStat },
    data(){
      return { 
        name : null, // Variables pour Afficher les infos sur poke
        type1 : null,
        type2 : null,
      }
    },
    methods :{
      // afficheStat(poke){  // Methode pour Afficher les infos sur poke
      //   this.name = poke.name;
      //   this.type1 = poke.type1;
      //   this.type2 = poke.type2;
      // }
    }
};
</script>

<style scoped>
.red:hover {
  transition-duration: 0.5s;
  background-color: rgb(100, 9, 9);
}

.green:hover {
  transition-duration: 0.5s;
  background-color: rgb(37, 74, 18);
}

.contain-pokeList {
  position : relative;
  width: 100%;
  height: 30vh;

  
  
}

.pokelist {
  position : absolute;
  left : 10%;
  width: 60vw;
  height: 30vh;
  overflow: auto;
  /* Mozilla firefox */
  scrollbar-color: #7b2cbf transparent;
  scrollbar-width: thin;
}
/* Global */
.pokelist::-webkit-scrollbar {
  width: 8px;
}
/* Ascenseur */
.pokelist::-webkit-scrollbar-thumb {
  background: #7b2cbf;
  border-radius: 8px;
}


.button {
    display : inline;
}
.contain-pokeList button {
  margin: 3px;
  background-color: #3c096c;
}
.contain-pokeList button img {
  width: 110px;
  height: 110px;
}

.displayStat{
  position: absolute;
  left :80%;
}
</style>