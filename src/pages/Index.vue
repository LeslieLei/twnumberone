<template>
  <q-page class="flex flex-center column" style="background-color:gray">
    <div class="container" id="twno1">
      <div class="green" style="width:100%;height:160px">
        &nbsp;
      </div>
      <div class="white" style="height: 30px">
        <div class="gray dot"></div>
      </div>
      <div class="green" style="width:100%;height:150px">
        <div class="white" style="width:30px;height:100%;margin-left:70px"></div>
        <div class="inputText">{{inputText}}</div>
      </div>
    </div>

    <q-card class="white" style="width: 500px; ">
      <div class="q-pa-sm">
        說明:於下方填寫文字後點選'輸出'按鈕 即可輸出圖片！
      </div>
      <div class="q-pa-sm">請大家持續支持我國選手!!</div>
      <q-input filled v-model="inputText" clearable label="填寫文字" />
      <q-btn class="q-pa-sm text-h6" dense round flat color="primary" icon="download" @click="download()">
        輸出
      </q-btn>
    </q-card>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue';
import * as htmlToImage from 'html-to-image';
import { saveAs } from 'file-saver';

export default defineComponent({
  name: 'PageIndex',
  data () {
    return {
      inputText: 'AIWAN No 1'
    }
  },
  methods: {
    download() {
      htmlToImage.toBlob(document.getElementById('twno1'),{ width: 500, height: 340, quality: 0.95, pixelRatio: 1})
        .then(function (dataUrl) {
          saveAs(dataUrl, 'twno1.png');
        });   
    }
    // download() {
    //   htmlToImage.toJpeg(document.getElementById('twno1'),{ width: 500, height: 340, quality: 0.95, pixelRatio: 1})
    //     .then(function (dataUrl) {
    //       const link = document.createElement('a');
    //       link.download = 'twno1.jpeg';
    //       link.href = dataUrl;
    //       link.click();
    //     });   
    // }    
  }
})
</script>
<style>
@font-face {
  font-family: 'Han';
  src: url(~assets/SourceHanSerifTC-Bold.otf);
}
.container {
  width: 500px;
  height: 350px;
  font-family: 'Han', 'Noto Sans TC', sans-serif;
}
.green {
  background-color: rgb(0, 123, 75);
}
.gray {
  background-color: rgb(112,115,114);
}
.white {
  background-color: white;
}
.dot {
  position:relative;
  top: 5px;
  left:180px;
  width:20px;
  height:20px;
  border-radius: 10px;
}
.inputText {
  position: relative;
  left: 150px;
  top: -100px;
  font-size: 28px;
  color: white;
}

</style>
