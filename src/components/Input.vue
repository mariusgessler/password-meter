<template>
  <div class='input__container' >
    <label for='password'>
      <input
        v-model='password'
        type='password'
        placeholder='Password'
        >
      </label>
    <pm-meter-bar :password='password' />
    </div>
</template>

<script>
import MeterBar from './MeterBar.vue';

export default {
  components: {
    'pm-meter-bar': MeterBar,
  },
  data() {
    return {
      password: '',
    };
  },
};
</script>

<style lang='scss'>
.input__container {
  padding: 45px;

  input {
    display: block;
    box-sizing : border-box;
    width: 100%;
    border: 0;
    outline: 0;
    border-radius: 15px;
    background-color: #EBECF0;
    font-family: 'DM Mono', monospace;
    letter-spacing: .3em;
    text-shadow: 1px 1px 0 #FFF;
    box-shadow:  inset 2px 2px 5px #BABECC, inset -5px -5px 10px #FFF;
    margin: 0 auto;
    padding: 15px 0 15px 25px ;
    transition: all 0.2s ease-in-out;
    appearance: none;
    -webkit-appearance: none;

    &:focus {
    box-shadow:  inset 1px 1px 2px #BABECC, inset -1px -1px 2px #FFF;
    }

    &::placeholder {
      text-transform: uppercase;
    }
  }
}
</style>
