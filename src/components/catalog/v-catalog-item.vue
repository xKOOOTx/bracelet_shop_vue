<template>
  <div class="v-catalog-item">
    <img :src=" require('../../assets/images/' + product_data.image)" alt="img" class="v-catalog-item__img">
    <p class="v-catalog-item__name">{{ product_data.name }}</p>
    <p class="v-catalog-item__price">Price: {{ product_data.price }} &#8381;</p>
    <button class="v-catalog-item__add_to_cart_btn btn"
            @click="addToCart()"
    >Add to cart</button>
  </div>
</template>

<script>
export default {
  name: 'v-catalog-item',
  props: {
    product_data: {
      type: Object,
      default() {
        return {}
      }
    },
  },
  methods: {
    addToCart() {
      this.$emit('addToCart', this.product_data)
    },
  },
  mounted() {
    this.$set(this.product_data, 'quantity', 1)
  }
}
</script>

<style lang="scss">
@import '../../assets/styles/variables';
 .v-catalog-item {
   flex-basis: 25%;
   box-shadow: $boxShadow;
   padding: $padding*2;
   margin: $margin*2;
   &__img {
     width: 100px;
   }
 }
</style>
