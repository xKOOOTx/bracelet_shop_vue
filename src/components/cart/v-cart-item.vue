<template>
  <div class="v-cart-item">
    <img class="v-cart-item__image"
         :src=" require('../../assets/images/leather/' + cart_item_data.image)"
         :alt="cart_item_data.name">
    <div class="v-cart-item__info">
      <p class="v-cart-item__name">{{ cart_item_data.name }}</p>
      <p class="v-cart-item__price">Price: {{ cart_item_data.price }} &#8381;</p>
      <p class="v-cart-item__article">Article: {{ cart_item_data.article }}</p>
    </div>
    <div class="v-cart-item__quantity">
      <p>Quantity:</p>
      <span class="v-cart-item__quantity_block">
        <span class="v-cart-item__quantity_btn" @click="decrementItem">-</span>
        {{ cart_item_data.quantity }}
        <span class="v-cart-item__quantity_btn" @click="incrementItem">+</span>
      </span>
    </div>
    <button class="btn" @click="deleteFromCart()">Delete</button>
  </div>
</template>

<script>

export default {
  name: 'v-cart-item',
  props: {
    cart_item_data: {
      type: Object,
      default() {
        return {}
      }
    }
  },
  methods: {
    deleteFromCart() {
      this.$emit('deleteFromCart')
    },
    decrementItem() {
      this.$emit('decrement')
    },
    incrementItem() {
      this.$emit('increment')
    },
  },
}
</script>

<style lang="scss">
@import '../../assets/styles/variables';

  .v-cart-item {
    display: flex;
    flex-wrap: nowrap;
    justify-content: space-between;
    align-items: center;
    margin: 10px;
    padding: 20px 10px;
    border: 1px solid #ccc;
    border-radius: $radius;
    transition: all .3s ease-in-out;
    &__image {
      width: 70px;
    }
    &__info {
      text-align: left;
      p {
        &:not(:last-child) {
          margin-bottom: 10px;
        }
      }
    }
    &:hover {
      box-shadow: $boxShadow;
      border-color: transparent;
    }
    &__quantity {
      &_block {
        display: flex;
        align-items: center;
        justify-content: center;
      }
      &_btn {
        margin: 10px;
        padding: 5px 15px;
        border: 1px solid #cccccc;
        border-radius: $radius;
        display: flex;
        align-items: center;
        justify-content: center;
        cursor: pointer;
        user-select: none;
        transition: all .3s ease-in-out;
        &:hover {
          background-color: #cccccc;
          color: #ffffff;
        }
      }
    }
  }
</style>
