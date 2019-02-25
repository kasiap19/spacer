<template>
     <div class="searchWrapper">
      <input id="search" name="search" v-model='searchValue' @input='handleInput' />
    </div>
</template>

<script>
import axios from 'axios';
import debounce from 'lodash.debounce';

const API = 'https://images-api.nasa.gov/search';

export default {
    name: 'SearchInput',
    data() {
    return {
      searchValue: '',
      results: [],
    }
  },
  methods: {
    handleInput: debounce(function(){
      axios.get(`${API}?q=${this.searchValue}&media_type=image`)
      .then((response) => {
        this.results = response.data.collection.items;
        console.log(this.results);
      })
      .catch((error) => {
        console.log(error)
      });
    }, 500)
  }
}
</script>

<style lang="scss" scoped>

 .searchWrapper {
    display: flex;
    flex-direction: column;
    width: 100%;
    margin-top: 50px;
    justify-content: center;
    align-items: center;
  }

  input {
    height: 30px;
    text-align: center;
    font-size: 18px;
    font-weight: 300;
    background: transparent;
    border: 0;
    color: #ddd;
    border-bottom: 1px solid #ddd;
    transition: box-shadow .5s;

    @media (min-width: 768px) {
        font-size: 24px;
        padding-bottom: 20px;
        width: 400px;
    }

    &::placeholder {
        color: white;
    }

    &:focus {
        outline: none;
        box-shadow: 0 10px 20px -8px rgba(255, 255, 255, .3);
    }
  }
</style>


