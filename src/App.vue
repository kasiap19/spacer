<template>
  <div id="app">
      <div class="wrapper">
        <Background />
      <Claim />
      <SearchInput />
    </div>
  </div>
</template>
<script>
import Claim from '@/components/Claim.vue';
import SearchInput from '@/components/SearchInput.vue';
import Background from '@/components/Background.vue';

const API = 'https://images-api.nasa.gov/search';
export default {
  components : {
    Background,
    Claim,
    SearchInput
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
    padding: 30px;
    width: 100%;
    justify-content: center;
    height: 100vh;
  }
 

</style>
