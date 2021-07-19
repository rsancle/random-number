<template>
  <h1>El Discurs</h1>
  <h2>{{ speech.title }}</h2>
  {{ speech.body }}
</template>

<script>
  export default {
    name: "Speech",
    props: {
      speech: Object,
    },
    emits: ["addColor"],
    mounted() {
      this.$emit("addColor", "default");
    },
  };
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
