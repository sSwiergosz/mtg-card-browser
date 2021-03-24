<template>
  <Wrapper>
    <h1>MTG search</h1>
    <InputContainer>
      <Input
        placeholder="Type card name here"
        v-model="cardName"
      />
      <button
        type="button"
        v-if="!isDataFetching"
        v-on:click="handleCardSearch"
      >
        Search!
      </button>
      <Loader v-if="isDataFetching" />
    </InputContainer>
    <SearchResultsPage
      v-bind:data="searchResults"
      v-bind:query="cardName"
      v-if="searchResults.length"
    />
  </Wrapper>
</template>

<script>
import styled from 'vue-styled-components';

import Loader from './Loader.vue';
import SearchResultsPage from './SearchResultsPage.vue';

const Input = styled.input`
  width: 200px;
  height: 30px;
  font-size: 16px;
`;

const InputContainer = styled.div`
  display: flex;

  & > input {
    margin-right: 20px;
  }
`;

const Wrapper = styled.div`
  display: flex;
  flex-direction: column;
  align-items: center;
`;

export default {
  name: 'SearchMainPage',
  components: {
    Input,
    InputContainer,
    Loader,
    SearchResultsPage,
    Wrapper,
  },
  data() {
    return {
      cardName: '',
      isDataFetching: false,
      searchResults: [],
    };
  },
  methods: {
    async handleCardSearch() {
      this.isDataFetching = true;
      const response = await fetch(`https://api.scryfall.com/cards/search?q=${this.cardName}`);
      const parsedResponse = await response.json();
      this.searchResults = parsedResponse.data;
      this.isDataFetching = false;
    },
  },
};
</script>
