<template>
  <h1>El Codi</h1>
  <p>
    El següent generador de números us ajudarà a desxifrar el codi que us
    proporcionarà accès al nostre apreciat regal. Un cop els tingueu tots, els
    haureu d'ordenar per trobar la combinació correcta:
  </p>
  <span class="number">{{ randomNumber }}</span>
</template>

<script>
  export default {
    name: "RandomCode",
    props: {
      code: Array,
    },
    emits: ["addColor"],
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
          this.$emit("addColor", "green");
          setTimeout(() => {
            this.$emit("addColor", "default");
            this.randomInterval();
          }, 3000);
        }, 8000);
      },
    },
  };
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .number {
    font-size: 50px;
    font-weight: 400;
    font-style: normal;
    line-height: 1.333;
  }
</style>
