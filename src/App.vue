<template>
  <div id="app">
    <div id="imgCont" v-if="jpg.length">
      <img v-for="img in jpg" :key="img" :src="img" />
    </div>
    <div v-else>
      loading
    </div>
  </div>
</template>

<script>
  const parser = new DOMParser();
import axios from "axios";
import "./h.js";
export default {
  name: "App",
  computed: {
    jpg() {
      return this.imgArr.filter(img => img.includes("jpg"));
    }
  },
  async mounted() {
    try {
  this.imgArr = await this.fetchImg().then(r => r.map(img => img.src)) || []
    } catch(err) {
      console.log(err)
    }
  },
  methods: {
    async fetchImg() {
      return await this.domPrsr("http://multi.xnxx.com");
    },
    async domPrsr(url) {
      try {

      
      let { data } = await axios.get(url);
      console.log(data)
      let d = parser.parseFromString(data, "text/html");
      return this.imgExtractor(d);}
      catch(err) {
        console.log(err)
        return []
      }
    },
    imgExtractor(domObj) {
      return Array.from(domObj.images);
    }
  },
  data() {
    return {
      cnt: 0,
      imgArr: []
    };
  }
};
</script>

<style scoped>
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
    width: 100vw;
    color: white;
  }

  #imgCont {
    background: black;
    display: grid;
    align-items: flex-start;
    grid-template-columns: repeat(10, 1fr);
  }

  img {
    width: 100%;
  }
</style>