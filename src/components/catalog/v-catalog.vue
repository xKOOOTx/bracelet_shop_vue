<template>
  <div class="v-catalog">
    <div class="v-catalog__link_to_cart">
        <p class="v-catalog__link_to_cart_link" @click="isCartPopupHidden = !isCartPopupHidden">Cart: {{ CART.length }}</p>
        <v-cart-popup v-show="isCartPopupHidden"
                      :popup_cart_data="CART"
        />
      </div>
    <h1>Catalog</h1>
    <div class="v-catalog__list" v-if="dataArrived">
      <v-catalog-item
          v-for="product in PRODUCTS"
          :key="product.article"
          :product_data="product"
          @addToCart="addToCart"
      />
    </div>
    <div
        v-else
        class="loader"
    ><img src="../../assets/images/loader.gif" alt="loader"></div>
  </div>
</template>

<script>
import vCatalogItem from './v-catalog-item';
import {mapActions, mapGetters} from 'vuex';
import VCartPopup from '../cart/v-cart-popup';

export default {
  name: 'v-catalog',
  components: {
    VCartPopup,
    vCatalogItem,
  },
  data() {
    return {
      products: [
        {
          image: "1.jpg",
          name: "T-shirt 1",
          price: 2100,
          article: "T1",
          available: true,
          category: "Мужские"
        },
        {
          image: "2.jpg",
          name: "T-shirt 2",
          price: 3150,
          article: "T2",
          available: true,
          category: "Женские"
        },
        {
          image: "3.jpg",
          name: "T-shirt 3",
          price: 4200,
          article: "T3",
          available: false,
          category: "Женские"
        },
        {
          image: "4.jpg",
          name: "T-shirt 4",
          price: 5300,
          article: "T4",
          available: true,
          category: "Мужские"
        },
        {
          image: "5.jpg",
          name: "T-shirt 5",
          price: 6500,
          article: "T5",
          available: false,
          category: "Женские"
        },
        {
          image: "6.jpeg",
          name: "T-shirt 6",
          price: 8700,
          article: "T6",
          available: true,
          category: "Женские"
        }
      ],
      dataArrived: false,
      isCartPopupHidden: false,
    }
  },
  computed: {
    ...mapGetters([
        'PRODUCTS',
        'CART'
    ]),
  },
  methods: {
    ...mapActions([
       'GET_PRODUCTS_FROM_API',
       'ADD_TO_CART',
    ]),
    addToCart(data) {
      this.ADD_TO_CART(data);
    },
    increment(index) {
      this.INCREMENT_CART_ITEM(index);
    },
    decrement(index) {
      this.DECREMENT_CART_ITEM(index);
    },
  },
  mounted() {
    this.GET_PRODUCTS_FROM_API()
    .then((response) => {
      if (response.data) {
        this.dataArrived = !this.dataArrived;
      }
    })
  }
}
</script>

<style lang="scss">
@import '../../assets/styles/variables';
  .v-catalog {
    &__list {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      align-items: center;
    }
    &__link_to_cart {
      position: absolute;
      top: 10px;
      right: 10px;
      padding: $padding*2;
      border-radius: $radius;
      border: 1px solid #cccccc;
      outline: none;
      transition: all .2s ease-in-out;
      user-select: none;
      cursor: pointer;
      &:hover,
      &:focus {
        background-color: darken(#ccc, 1%);
        .v-catalog__link_to_cart_link {
          color: #ffffff;
        }
      }
      &:active {
        background-color: darken(#ccc, 20%);
        .v-catalog__link_to_cart_link {
          color: darken(#ccc, 50%);
        }
      }
    }
  }
</style>
