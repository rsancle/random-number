<template>
  <main id="app">
    <section v-if="showRandom">
      <RandomCode :code="code" />
    </section>
    <section v-if="showMembers">
      <Members :members="members.sort()" />
    </section>
    <section v-if="showSpeach">
      <Speech :speech="speech" />
    </section>
    <ul>
      <li v-if="!showRandom">
        <button @click="toggle('showRandom')">Codi</button>
      </li>
      <li v-if="!showMembers">
        <button @click="toggle('showMembers')">Amics</button>
      </li>
      <li v-if="!showSpeach">
        <button @click="toggle('showSpeach')">Discurs</button>
      </li>
    </ul>
  </main>
</template>

<script>
  import RandomCode from "./components/RandomCode.vue";
  import Members from "./components/Members.vue";
  import Speech from "./components/Speech.vue";
  /* import CodeData from "./data/code.json";
  import SpeechData from "./data/speech.json";
  import MembersData from "./data/members.json"; */

  export default {
    name: "App",
    components: {
      RandomCode,
      Members,
      Speech,
    },
    data() {
      return {
        code: process.env.VUE_APP_CODE.split(","),
        speech: {
          title: process.env.VUE_APP_SPEECH_TITLE,
          body: process.env.VUE_APP_SPEECH_BODY,
        },
        members: process.env.VUE_APP_MEMBERS.split(","),
        showRandom: true,
        showMembers: false,
        showSpeach: false,
      };
    },
    methods: {
      toggle(button) {
        const value = !this[button];
        this.showRandom = false;
        this.showMembers = false;
        this.showSpeach = false;
        this[button] = value;
      },
    },
  };
</script>

<style>
  @font-face {
    font-family: "Playfair";
    src: local("Playfair"),
      url(./assets/fonts/PlayfairDisplay-VariableFont_wght.ttf)
        format("truetype");
  }
  h1 {
    font-size: 36px !important;
    font-weight: 400;
    font-style: normal;
    line-height: 1.333;
    font-size: 100%;
  }

  h2 {
    font-size: 25px !important;
    font-weight: 400;
    font-style: normal;
    line-height: 1.333;
    font-size: 100%;
  }
  #app {
    font-family: Playfair, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
  ul {
    list-style-type: none;
    padding: 0;
  }
  li {
    display: inline-block;
    margin: 0 10px;
  }
</style>
