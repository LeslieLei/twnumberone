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
      <div>填寫文字</div>
      <q-input filled v-model="inputText" label="填寫文字" />
        <q-btn class="text-h5" dense round flat color="primary" icon="add" @click="download()">
          下載
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
      htmlToImage.toJpeg(document.getElementById('twno1'),{ width: 500, height: 340, quality: 0.95, pixelRatio: 1})
        .then(function (dataUrl) {
          const link = document.createElement('a');
          link.download = 'my-image-name.jpeg';
          link.href = dataUrl;
          link.click();
        });   
    }    
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
  left:220px;
  width:20px;
  height:20px;
  border-radius: 10px;
}
.inputText {
  position: relative;
  left: 150px;
  top: -100px;
  font-size: 24px;
  color: white;
}

</style>
