<template>
  <div id="app">
    <div id="imgCont" v-if="jpg">
      <img v-for="img in jpg" :key="img" :src="img" />
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
      let { data } = await axios.get(this.url);
      let domObj = parser.parseFromString(data, "text/html");
  let arr = Array.from(domObj.images);
 this.imgArr = arr.map(img => img.src) }
     catch(err) {
      this.imgArr=err.message
    }
  },
  methods: {
    async fetchImg() {
      try {
      return await this.domPrsr("http://multi.xnxx.com");
      } catch(err) {
        this.msg=err
      }
    },
    async domPrsr(data) {
      let doc = parser.parseFromString(data, "text/html");
      return Array.from(doc.images);
    },
    imgExtractor(domObj) {
      return 
    }
  },
  data() {
    return {
      msg:"loading",
      cnt: 0,
      url:"https://multi.xnxx.com",
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
    grid-template-columns: repeat(20, 1fr);
  }

  img {
    width: 100%;
  }
</style>