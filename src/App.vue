<template>
  <div id="app">
    <h1><router-link to="/">Mo<img id="logo" alt="Vue logo" src="./assets/logo.png">ie DB</router-link></h1>
    <transition name="fade">
      <router-view />
    </transition>
  </div>
</template>

<script>


export default {
  name: 'app',
  data() {

  },
  components: {
  }
};
</script>

<style>
a{
  text-decoration: none;
  color: aliceblue;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
h1{
  color: aliceblue;
}
#logo{
  width:20px;
}

.fade-enter-active,
.fade-leave-active {
  transition: all 0.3s ease;
}
.fade-enter,
.fade-leave-to {
  opacity: 0;
  transform: scale(0);
}
</style>