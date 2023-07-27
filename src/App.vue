<script>
import axios from 'axios';
import BasePagination from './components/BasePagination.vue';
import SearchForm from './components/SearchForm.vue';
import AppHeader from './components/AppHeader.vue';
import { store } from './data/store';
import AppMain from './components/AppMain.vue';
export default {
  name: 'App',
  components: { AppHeader, AppMain, SearchForm, BasePagination },
  data() {
    return {
      apiBaseURI: 'https://41tyokboji.execute-api.eu-central-1.amazonaws.com/dev/api/v1/pokemons?per=20',
      apiURItype: 'https://41tyokboji.execute-api.eu-central-1.amazonaws.com/dev/api/v1/pokemons/types1',
      pokemonsTypes: [],
      typeFilter: '',
      nameFilter: '',
      store
    }
  },
  created() {
    this.fetchPokemonsList(this.apiBaseURI),
      this.fetchPokemonsType(this.apiURItype)
  },
  methods: {
    fetchPokemonsList(url) {
      store.isLoading = true;
      axios.get(url).then((res) => {
        store.pokemons = res.data.docs;
        const { hasPrevPage, hasNextPage, prevPage, nextPage } = res.data;
        store.pages = { hasPrevPage, hasNextPage, prevPage, nextPage };
      }).catch((err) => {
        console.error(err);
      }).then(() => {
        store.isLoading = false;
      });
    },
    fetchPokemonsType(url) {
      axios.get(url).then((res) => {
        this.pokemonsTypes = res.data;
      });
    },
    onSelectedType(type) {
      this.typeFilter = type;
      console.log(this.typeFilter);
    },
    onCickedButton(typeButton) {
      let url;
      typeButton === 'search' ? url = `${this.apiBaseURI}&eq[type1]=${this.typeFilter}` : url = this.apiBaseURI;
      this.fetchPokemonsList(url);
    },
    onTextChange(text) {
      this.nameFilter = text;
      const url = `${this.apiBaseURI}&q[name]=${this.nameFilter}`;
      this.fetchPokemonsList(url);
    },
    onChangePage(direction) {
      let url;
      if (direction === 'prev') {
        if (store.pages.hasPrevPage) url = `${this.apiBaseURI}&page=${store.pages.prevPage}`;
      } else {
        if (store.pages.hasNextPage) url = `${this.apiBaseURI}&page=${store.pages.nextPage}`;
      }
      this.fetchPokemonsList(url);
    }
  }
};
</script>

<template>
  <div class="container">
    <AppHeader></AppHeader>
    <SearchForm :typologies="pokemonsTypes" searchText="Cerca Pokemons" inputText="Cerca Pokemons attraverso il nome"
      @selected="onSelectedType" @search="onCickedButton('search')" clearText="Annulla" @clear="onCickedButton"
      @filteredText="onTextChange">
    </SearchForm>
    <BasePagination :prevDisabled="!store.pages.hasPrevPage" :nextDisabled="!store.pages.hasNextPage"
      @prev-Page="onChangePage('prev')" @next-Page="onChangePage('next')"></BasePagination>
    <AppMain></AppMain>
  </div>
</template>

<style lang="scss">
@use './assets/scss/style.scss' as *;
</style>