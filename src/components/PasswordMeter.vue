<template>
  <div class='password-meter__container'>
    <pm-input />
  </div>
</template>

<script>
import Input from './Input.vue';

export default {
  components: {
    'pm-input': Input,
  },
};

</script>

<style lang='scss'>
.password-meter__container {
  position: relative;
  left: 50%;
  top: 50%;
  max-width: 300px;
  transform: translate(-50%, -50%);
  border-radius: 25px;
  background: #EBECF0;
  background-image: url("../assets/clean-textile.png");
  box-shadow: 20px 20px 60px #c8c9cc,
             -20px -20px 60px #ffffff;
}
</style>
