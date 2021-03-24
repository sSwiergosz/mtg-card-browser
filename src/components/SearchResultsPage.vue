<template>
  <Wrapper>
    <h1>Results for "{{query}}":</h1>
    <ul>
      <StyledLi v-for="{
        flavor_text,
        mana_cost,
        name,
        id,
        image_uris: {
          small
        } = { small: '' },
        prices: {
          eur,
          eur_foil,
        }
      } in data" :key="id">
        <img :src="small" />
        <div>
          <StyledP>{{name}}</StyledP>
          <StyledP>Mana cost: {{mana_cost}}</StyledP>
          <FlavorText>{{flavor_text}}</FlavorText>
          <StyledP>Price trend (foil): {{eur}}€ ({{eur_foil}}€)</StyledP>
        </div>
      </StyledLi>
    </ul>
  </Wrapper>
</template>

<script>
import styled from 'vue-styled-components';

const FlavorText = styled.p`
  max-width: 300px;
  font-style: italic;
  text-align: left;
`;

const StyledLi = styled.li`
  display: flex;
  margin-bottom: 20px;
  list-style-type: none;

  & > img {
    margin-right: 20px;
  }
`;

const StyledP = styled.p`
  margin: 0;
  text-align: left;
`;

const Wrapper = styled.div`
  display: flex;
  flex-direction: column;
  align-items: center;
`;

export default {
  name: 'SearchResultsPage',
  components: {
    FlavorText,
    StyledLi,
    StyledP,
    Wrapper,
  },
  props: [
    'data',
    'query',
  ],
};
</script>
