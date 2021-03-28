<template>
  <div id="app">
    <imgs />
  </div>
</template>

<script>
  const parser = new DOMParser();
import imgs from './components/imgs.vue'
import "./h.js";
export default {
  name: "App",
  components:{imgs},
  computed: {
  },
  async mounted() {
  },
  methods: {
   
  },
  data(vm) {
    return {
    };
  }
};
</script>

<style type="scss">
  html,
  body {
    overflow: hidden;
    max-height: 100vh;
    min-height:100vh;
    margin: 0px;
    padding: 0px;
  }

  #app {
    background: black;
    min-height: 100%;
    width: 100vw;
    color: white;
  }

</style>