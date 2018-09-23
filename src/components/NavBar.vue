<template>
  <div class="navbar navbar-expand-lg navbar-light bg-light">
      <router-link v-bind:to="{ name: 'home' }" tag="button" class="btn btn-primary">Home</router-link>
      <router-link v-bind:to="{ name: 'about' }" tag="button" class="btn btn-primary">About</router-link>
    </div>
</template>

<script>
export default {
  name: 'NavBar',
  data() {
    return {};
  }
};
</script>

<style lang="scss">
.navbar {
  justify-content: center;
  padding: 30px;
  a {
    color: #2c3e50;
    margin-right: 20px;
    &.router-link-exact-active {
      color: #42b983;
    }
    &:last-child {
      margin-right: 0;
    }
  }
  .btn {
    margin-right: 10px;
    &:last-child {
      margin-right: 0;
    }
  }
}
</style>


