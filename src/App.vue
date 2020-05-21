<template>
  <div id="app">
    <PasswordMeter />
  </div>
</template>

<script>
import PasswordMeter from './components/PasswordMeter.vue';

export default {
  name: 'Password Meter',
  components: {
    PasswordMeter,
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=DM+Mono:wght@500&family=Roboto+Mono:wght@300&display=swap');

body {
  background-color: #EBECF0;
  background-image: url("./assets/clean-textile.png");
  margin: 0;
  height: 100vh;
}

#app {
  position: relative;
  top: 50%;
}
</style>
