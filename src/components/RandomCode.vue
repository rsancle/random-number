<template>
  <h1>El Codi</h1>
  <p>
    El següent generador de números us ajudarà a desxifrar el codi que us
    proporcionarà accès al nostre apreciat regal
  </p>
  <span>{{ randomNumber }}</span>
</template>

<script>
  export default {
    name: "RandomCode",
    props: {
      code: Array,
    },
    data() {
      return {
        randomNumber: 0,
        randomIntervalCallback: null,
        codeIntervalCallback: null,
      };
    },
    mounted() {
      this.randomInterval();
      this.codeInterval();
    },
    beforeUnmount() {
      clearInterval(this.randomIntervalCallback);
      clearInterval(this.codeIntervalCallback);
    },
    methods: {
      getRandom(min, max) {
        min = Math.ceil(min);
        max = Math.floor(max);
        return Math.floor(Math.random() * (max - min + 1) + min);
      },
      getRandomFromList(list) {
        return list[Math.floor(Math.random() * list.length)];
      },
      randomInterval() {
        this.randomIntervalCallback = setInterval(() => {
          let random = this.getRandom(1, 9);
          if (random == this.randomNumber) random = this.getRandom(1, 9);
          this.randomNumber = random;
        }, 100);
      },
      codeInterval() {
        this.codeIntervalCallback = setInterval(() => {
          clearInterval(this.randomIntervalCallback);
          this.randomNumber = this.getRandomFromList(this.code);
          this.$emit("addGreen");
          setTimeout(() => {
            this.$emit("clearGreen");
            this.randomInterval();
          }, 2000);
        }, 5000);
      },
    },
  };
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h3 {
    margin: 40px 0 0;
  }
  ul {
    list-style-type: none;
    padding: 0;
  }
  li {
    display: inline-block;
    margin: 0 10px;
  }
  a {
    color: #42b983;
  }
</style>
