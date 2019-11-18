<template>
  <div class="pos-rel">
    <div class="card" :class="!product.inStock && 'soldOut'">

      <img class="img" :src="getImageUrl(product.imageUrl)" alt="">
      <div class="text">
        <p class="bold">{{product.brandName}}</p>
        <p class="fw-500">{{product.productName}}</p>
        <p class="grey strike">Rs {{product.originalPrice}}</p>
        <p class="bold">Rs {{product.discountedPrice}}</p>
      </div>

    </div>

    <div class="sold-out-div" v-if="!product.inStock">
      <div class="sold-out-message" >
        <h5>FLASHSALE SOLD OUT</h5>
      </div>
    </div>

  </div>
</template>
<script>
export default {
  props: {
    product: Object
  },
  methods: {
    getImageUrl (url) {
      url = 'product-image.png'
      return require('../assets/images/' + url)
    }
  }
}
</script>
<style scoped lang="css">
.card {
  background: white;
  border: 1px solid black;
  margin: 20px;
  height: 350px;
  width: 200px;
  position: relative;
}
.card p {
    font-size: 13px;
    margin-bottom: 4px;
    margin-top: 4px;
}
.card .text {
    margin: 10px 10px;
}
.pos-rel {
  position: relative;
}
.img {
  width: 180px;
}
</style>
