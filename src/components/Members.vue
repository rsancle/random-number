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
    props: {
      members: Array,
    },
    mounted() {
      this.$emit("addColor");
    },
  };
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
