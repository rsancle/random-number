<template>
  <h1>El Codi</h1>
  <h2>{{ speech.title }}</h2>
  {{ speech.body }}
</template>

<script>
  export default {
    name: "Speech",
    props: {
      speech: Object,
    },
    mounted() {
      this.$emit("addColor");
    },
  };
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
