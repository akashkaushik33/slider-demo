<template>
  <div class="slider-wrapper pos-rel">
    <div class="slider ">
      <transition-group name="fade" class="d-flex" tag="div">
        <card v-for="(product, index) in products" :key="product.productName" v-show="isVisible(index)" :product="product"></card>
      </transition-group>
    </div>
    <button :disabled="slide === 0" @click="prevProductSlide" class="fab left">
      <img src="../assets/left-arrow.svg" alt="">
    </button>
    <button :disabled="slide === totalSlides" @click="nextProductSlide" class="fab right">
      <img src="../assets/right-arrow.svg" alt="">
    </button>
  </div>
</template>
<script>
import Card from './Card.vue'
export default {
  components: {
    Card
  },
  data: () => ({
    'productSlide': [],
    'slide': 0,
    'totalSlides': 0,
    'lastVisibleIndex': 0,
    'firstVisibleIndex': 0
  }),
  props: {
    products: Array
  },
  mounted () {
    this.totalSlides = Math.ceil(this.products.length / 2)
    // this.productSlide = this.products.slice(0, 5)
    this.lastVisibleIndex = 5
    this.firstVisibleIndex = 0
  },
  methods: {
    nextProductSlide () {
      this.slide += 1
      this.firstVisibleIndex = this.slide * 5
      this.lastVisibleIndex = this.firstVisibleIndex + 5
      // this.productSlide = this.products.slice((this.slide * 5), (this.slide * 5) + 5)
    },
    prevProductSlide () {
      this.slide -= 1
      this.firstVisibleIndex = this.slide * 5
      this.lastVisibleIndex = this.firstVisibleIndex + 5
      // this.productSlide = this.products.slice((this.slide * 5), (this.slide * 5) + 5)
    },
    isVisible (index) {
      console.log('!(index >= this.firstVisibleIndex && index < this.lastVisibleIndex)', (index >= this.firstVisibleIndex && index < this.lastVisibleIndex))
      return (index >= this.firstVisibleIndex && index < this.lastVisibleIndex)
    }
  }
}
</script>
<style lang="css">
  .slider {
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }
.fade-enter-active,
.fade-leave-active {
  transition: all 0.9s ease;
  overflow: hidden;
  visibility: visible;
  position: absolute;
  width:100%;
  opacity: 1;
}

.fade-enter,
.fade-leave-to {
  visibility: hidden;
  width:100%;
  opacity: 0;
}
.d-flex {
    display: flex;
  }
</style>
