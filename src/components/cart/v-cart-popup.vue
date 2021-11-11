<template>
  <div class="v-cart-popup">
    <ul class="v-cart-popup__list" v-if="popup_cart_data.length">
      <li class="v-cart-popup__list_element"
          v-for="(item, index) in popup_cart_data"
          :key="item.article">
        <img :src=" require('../../assets/images/' + item.image)"
             :alt="item.name"
             class="v-cart-popup__list_element_img">
        <div class="v-cart-popup__list_element_description">
          <p class="v-cart-popup__list_element_description_name">{{ item.name }}</p>
          <p class="v-cart-popup__list_element_description_article">{{ item.article }}</p>
        </div>
        <div class="v-cart-popup__list_element_quantity">
          <p class="v-cart-popup__list_element_quantity_buttons" @click="decrementItem(index)">-</p>
          <p class="v-cart-popup__list_element_quantity-amount">{{ item.quantity }}</p>
          <p class="v-cart-popup__list_element_quantity_buttons" @click="incrementItem(index)">+</p>
        </div>
      </li>
    </ul>
    <p v-else>Cart is empty</p>
    <router-link class="v-cart-popup__link"
                 :to="{name: 'cart', params: {cart_data: popup_cart_data}}"
    >
      <p>To cart</p>
    </router-link>
  </div>
</template>

<script>
import {mapActions, mapGetters} from 'vuex';

export default {
  name: "v-cart-popup",
  props: {
    popup_cart_data: {
      type: Array,
      default() {
        return []
      }
    },
  },
  methods: {
    ...mapActions([
        'ADD_TO_CART',
        'DELETE_FROM_CART',
        'INCREMENT_CART_ITEM',
        'DECREMENT_CART_ITEM'
    ]),
    ...mapGetters([
        'CART'
    ]),
    decrementItem(index) {
      console.log('decrement')
      this.$emit('decrement', index)
    },
    incrementItem(index) {
      console.log('increment')
      this.$emit('increment', index)
    },
  },
}
</script>

<style lang="scss">
@import './src/assets/styles/variables';
  .v-cart-popup {
    position: absolute;
    width: 400px;
    right: 10px;
    top: 50px;
    padding: 10px;
    background-color: #ffffff;
    box-shadow: $boxShadow;
    &__list {
      &_element {
        display: flex;
        justify-content: space-evenly;
        align-items: center;
        transition: all .2s ease-in-out;
        &:hover {
          border-radius: $radius;
          background-color: darken(#ffffff, 5%);
        }
        img {
          width: 50px;
          padding: $padding;
          margin: $margin;
        }
        &_description {
          display: flex;
          justify-content: center;
          align-items: center;
          flex: 2;
          p {
            padding: $padding;
            margin: $margin;
          }
        }
        &_quantity {
          display: flex;
          justify-content: space-between;
          align-items: center;
          flex: 1;
          margin-right: 15px;
          background-color: $white;
          border-radius: $radius;
          overflow: hidden;
          &_buttons {
            display: block;
            padding: 10px 15px;
            font-size: 20px;
            transition: all .2s ease-in-out;
            &:hover {
              background-color: darken($grey, 10%);
            }
          }
        }
      }
    }
    &__link {
      text-decoration: none;
      p {
        padding: $padding;
        margin: $margin;
        transition: background-color .2s ease-in-out;
        border-radius: $radius;
        &:hover {
          background-color: darken(#ffffff, 10%);
        }
      }

    }
  }
</style>
