<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<style lang="scss">
@import './style/variables';

#app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Ubuntu, Cantarell,
                "Helvetica Neue", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: $fontColor;
}

// main
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

a {
  text-decoration: none;
  &:hover {
    text-decoration: underline;
  }
}

li {
  list-style: none;
}

img {
  display: block;
}
</style>
