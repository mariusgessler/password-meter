<template>
  <p class='feedback'>{{ feedback }}</p>
</template>

<script>
export default {
  mounted() {
    document.addEventListener('keyup', () => {
      clearTimeout(this.timeout);
      this.timeout = setTimeout(() => {
        this.getFeedback();
      }, 500);
    });
  },
  methods: {
    getFeedback() {
      if (this.strength) {
        if (this.strength.feedback.warning) {
          this.feedback = `${this.strength.feedback.warning}.`;
        } else if (this.strength.feedback.suggestions[0]) {
          this.feedback = this.strength.feedback.suggestions[0];
        } else {
          this.feedback = `It would take approx. ${this.strength.guesses} attempts to guess this password.`;
        }
      } else {
        this.feedback = null;
      }
    },
  },
  props: {
    strength: {
      type: Object,
    },
  },
  data() {
    return {
      feedback: '',
      timeout: null,
    };
  },
};
</script>

<style>
.feedback {
  height: 50px;
  font-size: 14px;
  color: #757575;
  font-family: 'Roboto Mono', monospace;
  letter-spacing: 0.7px;
}
</style>
