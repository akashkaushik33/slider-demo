<template>
  <div class="slider-wrapper pos-rel">

    <div class="slider ">
      <transition-group class="d-flex" name="slide" tag="div">
        <div v-for="(product) in productSlide" :key="product.productName">
          <card :product="product"></card>
        </div>
      </transition-group>
    </div>

    <button
      :disabled="slide === 0"
      @click="prevProductSlide"
      class="fab left"
      :class="(slide === 0) && 'disabled-btn'"
    >
      <img src="../assets/images/left-arrow.svg" alt="">
    </button>

    <button
      :disabled="slide === totalSlides"
      @click="nextProductSlide"
      class="fab right"
      :class="(slide === totalSlides) && 'disabled-btn'"
    >
      <img src="../assets/images/right-arrow.svg" alt="">
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
    productSlide: [],
    slide: 0,
    totalSlides: 0
  }),
  props: {
    products: Array
  },
  mounted () {
    this.totalSlides = Math.ceil(this.products.length / 5) - 1
    this.productSlide = this.products.slice(0, 5)
  },
  methods: {
    nextProductSlide () {
      this.slide += 1
      this.productSlide = this.products.slice((this.slide * 5), (this.slide * 5) + 5)
    },
    prevProductSlide () {
      this.slide -= 1
      this.productSlide = this.products.slice((this.slide * 5), (this.slide * 5) + 5)
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
  overflow: hidden;
}
.disabled-btn {
  opacity: 0.2;
  cursor: not-allowed;
}
.d-flex {
  display: flex;
  overflow: hidden;
}
.slider-wrapper {
    margin-left: 20px;
    margin-right: 20px;
}

</style>
