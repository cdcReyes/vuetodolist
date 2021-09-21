<template>
  <div id="app">
    <Header />
    <router-view/>
  </div>
</template>

<script>
import Header from'./components/layout/Header';
export default {
  name:"app",
  components: {
    Header
  }
}
</script>

<style>
@font-face {
    font-family: 'eraserregular';
    src: url('~@/assets/eraserregular-webfont.woff2') format('woff2'),
         url('~@/assets/eraserregular-webfont.woff') format('woff');
    font-weight: normal;
    font-style: normal;

}

#app {
  font-family:'EraserRegular', Arial, Helvetica, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color:#ffffff ;
}

#nav a.router-link-exact-active {
  color: #1c2227;
}
</style>
