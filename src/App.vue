<template>
  <div id="app">
      <div :class="[{flexStart : step ==1}, 'wrapper']">
        <transition name="slide" v-if="step === 1">
          <h1 class="claim__title--dark">
            SPACER     
            <font-awesome-icon icon="space-shuttle" />
        </h1>
        </transition>
        <transition name="fade">
          <Background v-if="step === 0"/>
        </transition>
      <Claim v-if="step === 0" />
      <SearchInput v-model="searchValue" @input="handleInput" :dark="step === 1" />

      <div class="results" v-if="results && !loading && step ===1">
        <Item v-for="item in results" :item="item" @click.native="handleModalOpen(item)"/>
      <!-- <div class="loader" v-if="step===1 && loading===true"></div> -->
        <Modal v-if="modalOpen" :item="modalItem" @closeModal="modalOpen=false" @keydown.esc="modalOpen == false" />
      </div>
    </div>
  </div>
</template>
<script>
import axios from 'axios';
import debounce from 'lodash.debounce';

import Claim from '@/components/Claim.vue';
import SearchInput from '@/components/SearchInput.vue';
import Background from '@/components/Background.vue';
import Item from '@/components/Item.vue'
import Modal from '@/components/Modal.vue'

const API = 'https://images-api.nasa.gov/search';

export default {
  components : {
    Background,
    Claim,
    SearchInput,
    Item,
    Modal
  },

    data() {
    return {
      modalItem: null,
      modalOpen: false,
      loading: false,
      step: 0,
      searchValue: '',
      results: [],
    }
  },
  methods: {
    handleModalOpen(item) {
      this.modalOpen = true;
      this.modalItem = item;

      console.log(this.modalItem)
    },
    handleInput: debounce(function(){
      this.loading = true;
      console.log(this.searchValue);

      axios.get(`${API}?q=${this.searchValue}&media_type=image`)
      .then((response) => {
        this.results = response.data.collection.items;
        console.log(this.results);
        this.loading = false;
        this.step = 1;
      })
      .catch((error) => {
        console.log(error);
      });
    }, 500)
  },
}
</script>


<style lang="scss">
  @import url('https://fonts.googleapis.com/css?family=Montserrat:100,100i,200,200i,300,300i,400,400i,500,500i,600,600i,700,700i,800,800i,900,900i&subset=latin-ext');

  * {
    box-sizing: border-box;
  }

  body {
    font-family: 'Montserrat', sans-serif;
    margin: 0;
  }

   .wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
    min-height: 100vh;
    margin: 0;
    position: relative;
    padding: 30px;
    width: 100%;
    justify-content: center;
    height: 100vh;

    &.flexStart {
      justify-content: flex-start;
    }
  }
 
 .slide-enter-active, .slide-leave-active {
  transition: opacity .1s ease;
}
.slide-enter, .fade-leave-to {
  opacity: 0;
}

 .fade-enter-active, .fade-leave-active {
  transition: opacity .3s ease;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}

.logo {
  padding: 0 40px;
  position: absolute;
  top: 40px;
  width: 100%;
}

.results {
  display: grid;
  grid-gap: 20px;
  margin-top: 50px;

  @media (min-width: 768px) {
    grid-template-columns: repeat(3, 1fr);
  }
}

.loader {
  display: inline-block;
  width: 64px;
  margin-top: 100px;
  height: 64px;
}
.loader:after {
  content: " ";
  display: block;
  width: 46px;
  height: 46px;
  margin: 1px;
  border-radius: 50%;
  border: 5px solid black;
  border-color: black transparent black transparent;
  animation: loader 1.2s linear infinite;
}
@keyframes loader {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}



</style>
