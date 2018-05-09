<template>
  <div class="hello">
    <div>
        <button class="save-button"  @click="screenshots()">点击保存名片</button> 
        <div class="company-card-info center-father-style-align" ref="copyCardArea" id="copyCardArea">
          <div id="copyArea" class="copyArea" ref="copyArea">
            <div class="company-name-short">郁结</div>
            <div class="company-name-full">Alibaba iDST</div>
            <div class="company-connection">
              <div class="company-phone">
                <div class="inline-block company-phone-text">电话：</div>
                <div class="inline-block company-phone-number">*保密*</div>
              </div>
              <div>
                <div class="inline-block company-webmail-text">邮箱：</div>
                <div class="inline-block company-webmail-number">15114584731@163.com</div>
              </div>
            </div>
            <img width="100px;" height="200px;" src="https://img.alicdn.com/tfs/TB1tOvDXjuhSKJjSspjXXci8VXa-668-332.png" alt="">
          </div>
        </div>
        
        <h2>下面是截图部分：</h2>
        
        <div class="img-show" :style="{display: state.isDownloadImg ? 'block':'none'}">
          <img :src="state.imgUrl"/>
        </div>
      </div>
  </div>
</template>

<script>
import html2canvas from "html2canvas";
export default {
  name: 'HelloWorld',
  data () {
    return {
      state: {
        isDownloadImg: false,
        imgUrl: ''
      }
    }
  },
  methods: {
    screenshots() {
      let b64;
        html2canvas(this.$refs.copyCardArea, {
          useCORS: true
        }).then(canvas => {
          try {
            b64 = canvas.toDataURL("image/png");
          } catch (err) {
            console.log(err)
              alert(err)
          }
          this.state = {
            imgUrl: b64,
            isDownloadImg: true,
          }
        });
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.save-button{
  padding:10px 20px;
  margin:10px 120px;
}

.img-show{
  margin-top:20px;
}

.inline-block{
	display: inline-block;
}

.center-father-style-align{
	display: flex;
	align-items: center;
}

.company-card-info{
	color: white;	
	width: 334px;
	height: 166px; 
	
	border-radius: 5px;
	padding: 0 20px;

	background-image: url(https://test.wang-guanjia.com/static/img/d8aaea64-f72d-4faf-b79f-bd09af0bb08e.jpg);
	background-repeat: no-repeat;
}


.company-name-short{
	font-size: 20px;
	margin-bottom: 4.5px;
}

.company-name-full{
	font-size: 13px;
	color: #fff;
	opacity: 0.7;
}

.company-card-powerby-icon{
	margin-top: 60px;
	padding-bottom: 17.5px;
}

.powerby-icon svg{
	width: 116px;
	height: 12.5px;
}

.company-connection{
	margin-top: 23.5px;
}

.company-phone{
	margin-bottom: 2px;
}



.cover-grey{
	background-color: grey;
	opacity: 0.5;
	
  width: 100%;
  height: 100%;
  position: fixed;
  top: 0;
  left: 0;
}

.button-inside{
  position: fixed;
  
  bottom: 0;
	width: 100%;
	font-size: 18px;
	left: 0;
}

.cover-button-ul{
	border: 5px solid #fff;
	border-radius: 5px;
	margin: 0 20px;
}

.cover-button-ul li{
	border-bottom: 1px solid #D1D1D1;
}

.no-border{
	border: 0 !important;
}

.cover-button{
	background-color: #fff;
	color: #4A4A4A;
	width: 100%;
	text-align: center;
	padding: 10px 0;
}


.cover-button-cancel{
	border-radius: 5px;
}

.cover-button-cancel-a,
.cover-button-div{
	margin: 15px 20px;
}

.cover-button-div{
	background-color: #fff;
	border-radius: 5px;
	
	color: #4A4A4A;
	text-align: center;
	padding: 10px 0;
	font-size: 18px;
}

.company-webmail-text,
.company-phone-text{
	font-size: 11px;
	color: #fff;
	opacity: 0.4;
}


.company-phone-number,
.company-webmail-number{
	font-size: 13px;
}

.no-phone-number-top{
	padding-top: 20px;
}

.hint-tips{
	line-height: 3;
}
</style>
