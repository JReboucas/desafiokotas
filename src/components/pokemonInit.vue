<!-- Inicialização do app, atributos e metodos -->
<template>
  <div class="container">
    <h1>Pokemon desafio kotas</h1>
    <PokemonSearch 
      :apiUrl="apiUrl" 
      @setPokemonUrl="setPokemonUrl" />
    <PokemonList 
      :imageUrl="imageUrl" 
      :apiUrl="apiUrl"
      @setPokemonUrl="setPokemonUrl" />
    <PokemonDetail 
      v-if="showDetail"
      :pokemonUrl="pokemonUrl"
      :imageUrl="imageUrl"
      @closeDetail="closeDetail" />
  </div>
</template>

<!-- consumo da API pokeapi e importação de outras datas -->
<script>
  import PokemonSearch from './pokemonSearch.vue';
  import PokemonList from './pokemonList.vue';
  import PokemonDetail from './pokemonDetail.vue';
  export default {
    data: () => {
      return {
        imageUrl: 'https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/',
        apiUrl: 'https://pokeapi.co/api/v2/pokemon/',
        pokemonUrl: '',
        showDetail: false
      }
    },
    components: {
      PokemonSearch,
      PokemonList,
      PokemonDetail
    },
    methods: {
      setPokemonUrl(url) {
        this.pokemonUrl = url;
        this.showDetail = true;
      },
      closeDetail() {
        this.pokemonUrl = '';
        this.showDetail = false;
      }
    }
  }
</script>

<!-- CSS da Background, fonts, cores do background -->
<style lang="scss" scoped>
  @import url('https://fonts.googleapis.com/css?family=Acme');
  .container {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    padding: 10px;
    width: calc(100% - 20px);
    min-height: calc(100vh - 20px);
    background: radial-gradient(#fffb0c, #a02d00);
    font-family: 'Acme', arial;
    font-size: 1rem;
    font-weight: normal;
  }
  h1 { color: #efefef; }
</style>