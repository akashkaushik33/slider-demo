<template>
  <div id="app">
    <div class="flash-sale" >
      <card-slider :products="products" ></card-slider>
    </div>
  </div>
</template>

<script>
import CardSlider from './components/CardsSlider.vue'
import { products } from './data'

export default {
  name: 'app',
  components: {
    CardSlider
  },
  data: () => ({
    products
  })
}
</script>

<style>
@import 'assets/stylesheets/main.css';
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* margin-top: 60px; */
  display: flex;
  align-items: center;
  height: 100vh;
  width: 100%;
}
.flash-sale {
  background-image: url('./assets/images/Background.png');
  display: flex;
  justify-content: center;
  align-items: center;
  height: 500px;
  width: 100%
}
</style>
