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
        allowTaint: true,
        // foreignObjectRendering: true,
      }).then(canvas => {
        // 特殊情况，如果需要使用 toDataURL() 方法转成 img 标签显示，则必须保证图片能够跨域（需要图片服务器添加Access-Control-Allow-Origin: *），并打开上方的 foreignObjectRendering 配置
        // let img = new Image();
        // img.src = canvas.toDataURL();
        // document.getElementById('result').appendChild(img);

        // 正常情况，即使是跨域图片也能在 canvas 中显示，右键也能保存为图片，可通过设置 style 修改样式，满足需求
        // 推荐使用以下方式实现
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
