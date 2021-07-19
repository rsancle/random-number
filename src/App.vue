<template>
  <main :class="backgroundClass">
    <section v-if="showRandom">
      <RandomCode :code="code" @add-color="addColor" />
    </section>
    <section v-if="showMembers">
      <Members :members="members.sort()" @add-color="addColor" />
    </section>
    <section v-if="showSpeach">
      <Speech :speech="speech" @add-color="addColor" />
    </section>
    <ul>
      <li>
        <button class="btn" @click="toggle('showRandom')">El Codi</button>
      </li>
      <li>
        <button class="btn" @click="toggle('showMembers')">Els Amics</button>
      </li>
      <li>
        <button class="btn" @click="toggle('showSpeach')">El Discurs</button>
      </li>
    </ul>
  </main>
</template>

<script>
  import RandomCode from "./components/RandomCode.vue";
  import Members from "./components/Members.vue";
  import Speech from "./components/Speech.vue";

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
        backgroundClass: "background-default",
      };
    },
    methods: {
      toggle(button) {
        this.showRandom = false;
        this.showMembers = false;
        this.showSpeach = false;
        this[button] = true;
      },
      addColor(color) {
        this.backgroundClass = "background-" + color;
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
  @font-face {
    font-family: "Roboto";
    src: local("Roboto"),
      url(./assets/fonts/Roboto-Medium.ttf) format("truetype");
  }
  h1 {
    margin-top: 0;
    font-size: 36px !important;
    font-weight: 400;
    font-style: normal;
    line-height: 1.333;
    font-size: 100%;
    font-family: Playfair, Helvetica, Arial, sans-serif;
  }

  h2 {
    font-size: 25px !important;
    font-weight: 400;
    font-style: normal;
    line-height: 1.333;
    font-size: 100%;
    font-family: Playfair, Helvetica, Arial, sans-serif;
  }
  p {
    font-size: 20px;
  }

  body {
    margin: 0;
  }

  section {
    padding: 60px 25px;
  }

  main {
    height: 100vh;
  }

  .btn {
    padding: 10px 25px;
    font-family: "Roboto", sans-serif;
    font-weight: 500;
    background: transparent;
    outline: none !important;
    cursor: pointer;
    transition: all 0.3s ease;
    position: relative;
    display: inline-block;
    border: 2px solid #000;
    z-index: 1;
    font-size: 15px;
  }

  /**** BTN No. 12 ****/
  .btn {
  }
  .btn:after {
    position: absolute;
    content: "";
    width: 100%;
    height: 0;
    bottom: 0;
    left: 0;
    z-index: -1;
    background: #000;
    transition: all 0.3s ease;
  }
  .btn:hover {
    color: #fff;
  }
  .btn:hover:after {
    top: 0;
    height: 100%;
  }
  .btn:active {
    top: 2px;
  }

  #app {
    font-family: Roboto, Playfair, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
  }
  ul {
    list-style-type: none;
    padding: 0;
  }
  li {
    display: inline-block;
    margin: 0 10px;
  }
  .background-default {
    background: #f5e3b1;
  }

  .background-green {
    opacity: 1;
    animation: fade 3s ease-in;
    background: #f5e3b1;
  }
  @keyframes fade {
    0%,
    100% {
      background: #f5e3b1;
    }
    25%,
    75% {
      background: #bff5b1;
    }
  }
</style>
