<template>
  <div class='meter-bar'>
    <div class='meter-bar__container'>
      <div :class='["meter-bar__fill", getFill() ]' />
    </div>
    <Feedback :strength='strength' />
  </div>
</template>

<script>
import zxcvbn from 'zxcvbn';
import Feedback from './Feedback.vue';

export default {
  components: {
    Feedback,
  },
  props: {
    password: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      strength: {},
      strengthLevel: '',
    };
  },
  watch: {
    password(input) {
      this.getStrength(input);
    },
  },
  methods: {
    getStrength(input) {
      if (input) {
        const strength = zxcvbn(input);
        this.strength = strength;
      } else {
        this.strength = null;
      }
    },
    getFill() {
      let strengthLevel = '';

      if (this.strength) {
        switch (this.strength.score) {
          case 0:
            strengthLevel = 'very_low';
            break;
          case 1:
            strengthLevel = 'low';
            break;
          case 2:
          case 3:
            strengthLevel = 'moderate';
            break;
          case 4:
            strengthLevel = 'high';
            break;
          default:
            strengthLevel = '';
        }
      }
      return strengthLevel;
    },
  },
};
</script>

<style lang='scss'>
.meter-bar__container {
  position: relative;
  width: 100%;
  max-width: 410px;
  height: 8px;
  background: #EBECF0;
  margin-top: 20px;
  border-radius: 12px;
  box-shadow: 3px 3px 6px #c8c9cc,
             -3px -3px 6px #ffffff;

  &:before,
  &:after {
    position: absolute;
    content: '';
    display: block;
    width: 25%;
    height: 100%;
    background-color: transparent;
    z-index: 2;
  }

  &:before {
    left: 25%;
    border-width: 0 0 0 5px;
  }

  &:after {
    right: 25%;
    border-width: 0 5px 0 5px;
  }

  .meter-bar__fill {
    position: absolute;
    background: transparent;
    height: inherit;
    width: 0;
    border-radius: 8px;
    transition: width .5s ease-in-out, background .3s;

    &.very_low {
      background: linear-gradient(90deg, #FFB3BA 0%, #ffdaba 100%);
      width: 25%;
    }

    &.low {
      background: linear-gradient(90deg, #ffdaba 0%, #FFFFBA 100%);
      width: 50%;
    }

    &.moderate {
      background: linear-gradient(90deg, #FFFFBA 0%, #baffc9 100%);
      width: 75%;
    }
    &.high {
      background: linear-gradient(90deg, #baffc9 0%, #77dd77 100%);
      width: 100%;
    }
  }
}
</style>
