<template>
  <header class="header">
    <div class="header__wrapper">
      <div class="header__logoBlock">
        <router-link to="/" class="header__logoBlock_link">
          <img src="https://via.placeholder.com/50" alt="logo" class="header__logoBlock_img">
        </router-link>
      </div>
      <div class="header__menuIcons">
        <div class="header__menuIcons_block">
          <svg class="header__menuIcons_profileBtn svg-inline--fa fa-user fa-w-14"
               aria-hidden="true" focusable="false" data-prefix="fas" data-icon="user"
               role="img" xmlns="http://www.w3.org/2000/svg"
               viewBox="0 0 448 512">
            <path fill="currentColor" d="M224 256c70.7 0 128-57.3 128-128S294.7 0 224 0 96 57.3 96
                                        128s57.3 128 128 128zm89.6 32h-16.7c-22.2 10.2-46.9 16-72.9
                                        16s-50.6-5.8-72.9-16h-16.7C60.2 288 0 348.2 0 422.4V464c0
                                        26.5 21.5 48 48 48h352c26.5 0 48-21.5
                                        48-48v-41.6c0-74.2-60.2-134.4-134.4-134.4z">
            </path>
          </svg>
          <svg class="header__menuIcons_cartBtn svg-inline--fa fa-shopping-cart fa-w-18"
               aria-hidden="true" focusable="false" data-prefix="fas" data-icon="shopping-cart"
               role="img"
               xmlns="http://www.w3.org/2000/svg" viewBox="0 0 576 512">
            <path fill="currentColor" d="M528.12 301.319l47.273-208C578.806 78.301 567.391 64 551.99
                                        64H159.208l-9.166-44.81C147.758 8.021 137.93 0 126.529
                                        0H24C10.745 0 0 10.745 0 24v16c0 13.255 10.745 24 24
                                        24h69.883l70.248 343.435C147.325 417.1 136 435.222 136
                                        456c0 30.928 25.072 56 56 56s56-25.072
                                        56-56c0-15.674-6.447-29.835-16.824-40h209.647C430.447
                                        426.165 424 440.326 424 456c0 30.928 25.072 56 56
                                        56s56-25.072
                                        56-56c0-22.172-12.888-41.332-31.579-50.405l5.517-24.
                                        276c3.413-15.018-8.002-29.319-23.403-29.319H218.117l-6.
                                        545-32h293.145c11.206 0 20.92-7.754 23.403-18.681z">

            </path>
          </svg>
          <svg @click="mobileMenu = !mobileMenu"
               id="openMobileMenuBtn"
               aria-hidden="true" focusable="false" data-prefix="fas" data-icon="bars"
               class="header__menuIcons_mobileMenuBtn svg-inline--fa fa-bars fa-w-14"
               role="img" xmlns="http://www.w3.org/2000/svg"
               viewBox="0 0 448 512">
            <path fill="currentColor"
                  d="M16 132h416c8.837 0 16-7.163 16-16V76c0-8.837-7.163-16-16-16H16C7.163 60 0
                    67.163 0 76v40c0 8.837 7.163 16 16 16zm0 160h416c8.837 0 16-7.163
                    16-16v-40c0-8.837-7.163-16-16-16H16c-8.837 0-16 7.163-16 16v40c0
                    8.837 7.163 16 16 16zm0 160h416c8.837 0 16-7.163
                    16-16v-40c0-8.837-7.163-16-16-16H16c-8.837 0-16 7.163-16
                    16v40c0 8.837 7.163 16 16 16z">
            </path>
          </svg>
        </div>
      </div>
      <div class="header__mobileMenuBtn">

      </div>
      <div class="header__mobileMenu" v-if="mobileMenu == true">
        <div class="header__mobileMenu_header">
          <img src="../assets/mobileMenu/closeMobileMenu.svg"
               alt="closeMobileMenu"
               class="header__mobileMenuBtn_img"
               id="closeMobileMenuBtn"
               @click="mobileMenu = !mobileMenu">
        </div>
        <div class="header__mobileMenu_main">
          <ul class="header__mobileMenu__list"
              v-for="(el, idx) in mobileMenuLinks"
              :key="idx"
          >
            <li class="header__mobileMenu__list_element"
                @click="consoleClicked(el)">{{ el.name }}</li>
          </ul>
        </div>
        <div class="header__mobileMenu_footer">
          <div class="header__mobileMenu_footer_left">
            <div class="header__mobileMenu_footer_left_logo">
              <img src="https://via.placeholder.com/50.png/fff" alt="logo" class="header__mobileMenu_footer_left_logo_img">
            </div>
          </div>
          <div class="header__mobileMenu_footer_right">
            <p>created and designed by Alex Gusev</p>
            <p>&copy;2021</p>
          </div>
        </div>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header',
  data() {
    return {
      mobileMenu: false,
      mobileMenuLinks: [
        {
          name: 'element1',
        },
        {
          name: 'element2',
        },
        {
          name: 'element3',
        },
        {
          name: 'element4',
        },
        {
          name: 'element5',
        },
      ],
    };
  },
  methods: {
    consoleClicked(el) {
      //  eslint-disable-next-line
      console.log(el.name);
    },
  },
};
</script>

<style scoped lang="scss">
@import '../style/variables';

.header {
  position: relative;
  width: 100%;
  background-color: darken($white, 10%);
  box-shadow: 3px 2px 8px rgba($black, .2);
  &__wrapper {
    max-width: 1200px;
    height: auto;
    margin: 0 auto;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  &__logoBlock {
    display: inline-block;
    height: 100%;
    &_link {
      height: 100%;
      width: 50px;
    }
    &_img {
      height: 100%;
      margin: 0 40px;
    }
  }
  &__menuIcons {
    display: flex;
    justify-content: flex-end;
    width: 100%;
    &_block {
      display: flex;
    }
    &_profileBtn,
    &_cartBtn,
    &_mobileMenuBtn {
      width: 20px;
      height: auto;
      margin: 0 40px;
      cursor: pointer;
      path {
        transition: fill .2s ease-in-out;
      }
      &:hover {
        path {
          fill: blue;
        }
      }
    }
    &_mobileMenuBtn {
      display: none;
    }
  }
  &__mobileMenu {
    position: absolute;
    top: 0;
    left: 0;
    display: flex;
    flex: 1;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    width: 100%;
    height: 100vh;
    padding: 20px;
    background-color: $grey;
    &__list {
      display: flex;
      flex-direction: column;
      justify-content: space-evenly;
      align-items: center;
      height: 100%;
      &_element {
        width: 70vw;
        padding: 20px 0;
        text-align: center;
        border-radius: 20px;
        background-color: darken($grey, 10%);
        text-transform: capitalize;
      }
    }
    &_header {
      display: flex;
      justify-content: flex-end;
      width: 100%;
    }
    &_main {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      height: 100%;
      width: 100%;
    }
    &_footer {
      height: 50px;
      width: 100%;
      margin: 0 auto;
      max-width: 530px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      &_left {
        &_logo {
          border-radius: 50%;
          overflow: hidden;
        }
      }
      &_right {
        display: flex;
        p {
          &:first-child {
            margin-right: 10px;
          }
        }
      }
    }
  }
}

@media (max-width: 800px) {
  .header {
    &__menuIcons {
      &_mobileMenuBtn {
        display: flex;
      }
    }
  }
}
</style>
