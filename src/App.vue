<template>
  <h1>Compose ton équipe</h1>
  <div class="main-containt">
    <ButtonReset class="button-reset-main" v-if="this.pokemonChoosen.length > 0" @ButtonReset="resetPokemonChoosen" />
    <DisplayStat
      class="displayStat"
      :name="name"
      :type1="type1"
      :type2="type2"
    />  
    <h2>Choisis tes Pokemon Mec:</h2>
    <PokeList
      :PokemonList="pokemonList"
      :IfSelected="false"
      :Color="'green'"
      @choosen-pokemon="addPokemon"
      @show-stat="showStat"
      @unShow-stat="this.name = null"
    />
    <br />  <!-- IfSelected sert a corriger un probleme d'affichage sur les pokemon choisis -->
    <h2>Tes Pokemon :</h2>
    <PokeList 
      :PokemonList="pokemonChoosen"
      :IfSelected="true"  
      :Color="'red'"
      @choosen-pokemon="delPokemon"
      @show-stat="showStat"
      @unShow-stat="this.name = null"
    />
  </div>
</template>

<script>
import DisplayStat from "./components/DisplayStat.vue";
import PokeList from "./components/PokeList.vue";
import ButtonReset from "./components/ButtonReset.vue";

export default {
  name: "App",
  components: {
    PokeList,
    DisplayStat,
    ButtonReset,
  },
  data() {
    return {
      pokemonList: [
        {
          id: 0,
          name: "Dracolosse",
          type1: "Dragon",
          type2: "Vol",
          img: "/images/Dracolosse.png",
          selected: false,
        },
        {
          id: 1,
          name: "Dracaufeu",
          type1: "Feu",
          type2: "Vol",
          img: "/images/Dracaufeu.png",
          selected: false,
        },
        {
          id: 2,
          name: "Alakazam",
          type1: "Psy",
          type2: null,
          img: "/images/Alakazam.png",
          selected: false,
        },
        {
          id: 3,
          name: "Dardagnan",
          type1: "Insect",
          type2: "Poison",
          img: "/images/Dardagnan.png",
          selected: false,
        },
        {
          id: 4,
          name: "Ectoplasma",
          type1: "Spectre",
          type2: "Poison",
          img: "/images/Ectoplasma.png",
          selected: false,
        },
        {
          id: 5,
          name: "Florizarre",
          type1: "Plante",
          type2: "Poison",
          img: "/images/Florizarre.png",
          selected: false,
        },
        {
          id: 6,
          name: "Galopa",
          type1: "Feu",
          type2: null,
          img: "/images/Galopa.png",
          selected: false,
        },
        {
          id: 7,
          name: "Leviator",
          type1: "Eau",
          type2: "Vol",
          img: "/images/Leviator.png",
          selected: false,
        },
        {
          id: 8,
          name: "Mackogneur",
          type1: "Combat",
          type2: null,
          img: "/images/Mackogneur.png",
          selected: false,
        },
        {
          id: 9,
          name: "Magneton",
          type1: "Electrik",
          type2: "Acier",
          img: "/images/Magneton.png",
          selected: false,
        },
        {
          id: 10,
          name: "Melodelf",
          type1: "Fee",
          type2: null,
          img: "/images/Melodelf.png",
          selected: false,
        },
        {
          id: 11,
          name: "Nidoking",
          type1: "Sol",
          type2: "Poison",
          img: "/images/Nidoking.png",
          selected: false,
        },
        {
          id: 12,
          name: "Papillusion",
          type1: "Insect",
          type2: "Vol",
          img: "/images/Papillusion.png",
          selected: false,
        },
        {
          id: 13,
          name: "Staross",
          type1: "Psy",
          type2: "Eau",
          img: "/images/Staross.png",
          selected: false,
        },
        {
          id: 14,
          name: "Tartard",
          type1: "Eau",
          type2: "Combat",
          img: "/images/Tartard.png",
          selected: false,
        },
        {
          id: 15,
          name: "Tortank",
          type1: "Eau",
          type2: null,
          img: "/images/Tortank.png",
          selected: false,
        },
        {
          id: 16,
          name: "Voltali",
          type1: "Electrik",
          type2: null,
          img: "/images/Volatli.png",
          selected: false,
        },
      ],
      pokemonChoosen: [],
      name: null, // Variables pour Afficher les infos sur poke
      type1: null,
      type2: null,
    };
  },
  methods: {
    addPokemon(poke) {
      if (this.pokemonChoosen.length < 6 && !poke.selected) {
        this.pokemonChoosen.push(poke); // Ajout du pokemon dans PokemonChoosen
        this.pokemonList[poke.id].selected = true;
      } else {
        alert("Equipe pleine");
      }
    },
    showStat(poke) {
      // Methode pour Afficher les infos sur poke
      this.name = poke.name;
      this.type1 = poke.type1;
      this.type2 = poke.type2;
    },

    delPokemon(poke) {
      console.log(this.pokemonChoosen.indexOf(poke));
      this.pokemonChoosen.splice(this.pokemonChoosen.indexOf(poke), 1);
      poke.selected = false;
    },
    resetPokemonChoosen() {
      if(confirm("Validez pour supprimer l'équipe...")){
        this.pokemonChoosen.forEach((poke) => (poke.selected = false));
        this.pokemonChoosen.splice(0, 6);
        console.log(this.pokemonChoosen.length);
      }
    },
  },
};
</script>

<style>
body {
  background-color: #10002b;
  color: #e0aaff;
  font-family: "Courier New", Courier, monospace;
  margin: 0px;
  padding: 0px;
  scrollbar-color: #7b2cbf transparent;
  scrollbar-width: thin;
}
/* Global */
body::-webkit-scrollbar {
  width: 8px;
}
/* Ascenseur */
body::-webkit-scrollbar-thumb {
  background: #7b2cbf;
  border-radius: 8px;
}
h1 {
  position: fixed;
  width: 100%;
  top: 0px;
  margin-bottom: 6vh;
  margin-top: 0px;
  padding-top: 3vh;
  padding-bottom: 3vh;
  text-transform: uppercase;
  font-weight: bold;
  border-bottom: 3px solid #e0aaff;
  text-align: center;
  background-color: #240046;
  z-index: 100;
}

h2 {
  font-family: "Courier New", Courier, monospace;
  position: relative;
  width: 90%;
  left: 10%;
}

.main-containt {
  position: relative;
  top: 14vh;
  width: 100%;
  height: 850px;
}

.displayStat {
  position: absolute;
  left: 75%;
  top: 20%;
}
</style>
