<template>
  <div id="app">
    <NavBar />
    <router-view/>
  </div>
</template>

<script>
import NavBar from '@/components/NavBar';

export default {
  name: 'App',
  data() {
    return {};
  },
  components: {
    NavBar
  }
};
</script>


<style lang="scss">
#app {
  font-family: 'Roboto', sans-serif;
  font-size: 14px;
  font-weight: 400;
  line-height: 21px;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #5b5b5b;
  background-color: #eee;
}
.btn-primary {
  padding: 5px 20px;
  background-color: cornflowerblue;
}
</style>
