<template>
  <div id="app">
    <pre>{{ pre }}</pre>
  </div>
</template>

<script>
  import axios from 'axios'
  import './h.js'
  console.log(axios)
  export default {
  name: "App",
  components: {},
 async mounted() {
let {data}= await axios.get('https://multi.xnxx.com/')
  },
  
data() {
  imgArr: [],
    imgArr: [],
}
},
 
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