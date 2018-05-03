<template>
  <div class="hello">
    <div id="test-target">
      <h1>测试</h1>
        <img src="../assets/logo.png" alt="同源的图片">
        <img src="https://deltice.github.io/jest/img/logos/facebook.png">
        <img src="https://www.web-tinker.com/pictures/7002e5d0eb969e981cd5d739ed54be79.png">
        <a href="javascript:;">test</a>
    </div>
    <button @click="screenshots()">截图</button>
    <div id="result"></div>
  </div>
</template>

<script>
import html2canvas from "html2canvas";
export default {
  name: 'HelloWorld',
  data () {
    return {
    }
  },
  methods: {
    screenshots() {
      html2canvas(document.getElementById('test-target'), {
        useCROS:true,
        allowTaint: true
      }).then(canvas => {
        canvas.style = ``;
        document.getElementById('result').appendChild(canvas);
      });
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
