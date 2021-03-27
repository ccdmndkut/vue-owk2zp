<template>
  <div id="app">
    <pre>{{ pre }}</pre>
  </div>
</template>

<script>
  export default {
  name: "App",
  components: {},
 async mounted() {
await fetch('http://example.com/movies.json')
  .then(response => response.json())
  .then(data => console.log(data));
  },
  data() {
    return {
      imgArr: [],
      pre: "pre"
    };
  }
};
</script>

<style scoped type="scss">
  html,
body {
  height: 100vh;
  overflow: hidden;
  max-height: 100vh;
  margin: 0px;
  padding: 0px;
}
  * {
    margin: 0px;
  }
#app {
  background: black;
  min-height: 100%;

}
</style>