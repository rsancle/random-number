<template>
  <h1>Els Amics</h1>
  <p>Aquest regal ha estat posible gràcies als vostres amics:</p>
  <ul>
    <li v-for="(member, index) in members" :key="index">{{ member }}</li>
  </ul>
</template>

<script>
  export default {
    name: "Members",
    emits: ["addColor"],
    props: {
      members: Array,
    },
    mounted() {
      this.$emit("addColor", "default");
    },
  };
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  li {
    display: block;
    padding: 7px;
    font-family: Playfair, Helvetica, Arial, sans-serif;
    font-size: 20px;
  }
</style>
