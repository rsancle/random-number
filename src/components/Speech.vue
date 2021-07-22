<template>
  <h1>El Discurs</h1>
  <div v-html="speech.body" class="speech-body"></div>
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
<style scoped>
  .speech-body {
    padding: 0 25%;
    text-align: left;
  }
</style>
