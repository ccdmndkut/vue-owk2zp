<template>
  <div id="app">
    <div class="imgCont" v-if="jpg">
      <img v-for="img in jpg" :key="img" :src="img" />
    </div>
  </div>
</template>

<script>
  const parser = new DOMParser();
import axios from "axios";
import Macy from 'macy'
export default {
  name: "Imgs",
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
    } finally {
      var macyInstance = Macy({
  container:'.imgCont'
});

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
  data(vm) {
    return {
      msg:"loading",
      cnt: 0,
      url:"https://www.eatliver.com/page/1/",
      imgArr: []
    };
  }
};
</script>

<style scoped type="scss">
  #imgCont {
    background: black;
    display: grid;
    align-items: flex-start;
    grid-template-columns: repeat(20, 1fr);

  }
   #imgCont {
     &img {
    width: 100%;
     }
  }
  .imgCont {
    max-height: 100vh;
    min-height:100vh;
    overflow: scroll;
  }


</style>