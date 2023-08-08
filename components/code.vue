<template>
  <div>
    <QRCodeVue3
      :width="data.width"
      :height="data.height"
      value="https://interactivesystems.pl/"
      :qrOptions="{ typeNumber: 0, mode: 'Byte', errorCorrectionLevel: 'H' }"
      :image-options="{ hideBackgroundDots: true, imageSize: 0.4, margin: 10 }"
      :corners-square-options="{ type: 'dot', color: '#03afd0' }"
      :corners-dot-options="{
        type: undefined,
        color: '#0089b4',
      }"
      :dots-options="{
        type: 'dots',
        color: '#41B883',
        gradient: {
          type: 'linear',
          rotation: 0,
          colorStops: [
            { offset: 0, color: '#03afd0' },
            { offset: 1, color: '#0089b4' },
          ],
        },
      }"
      image="/apple-touch-icon.png"
      fileExt="png"
      imgclass="img-qr"
      :downloadOptions="{ name: 'twoj-qr-code', extension: 'png' }"
    />
    <button class="download" @click="download">Pobierz</button>
    <div class="result" style="margin-top: 20px">
      <code>{{ data }}</code>
    </div>
  </div>
</template>

<script setup>
import QRCodeVue3 from "qrcode-vue3";
const { data } = defineProps({
  data: {
    type: Object,
    required: true,
  },
});
const download = () => {
  const imgList = window.document.getElementsByClassName("img-qr");
  let imagePath = imgList[0].getAttribute("src");

  let im = document.createElement("a");
  im.href = imagePath;
  im.target = "_blank";
  im.download = "QR-code-IS";
  document.body.appendChild(im);
  im.click();
  document.body.removeChild(im);
};
</script>

<style>
.download {
  margin-top: 30px;
  height: 30px;
  width: 150px;
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
  color: #383837;
  font-size: 16px;
  font-weight: bold;
  line-height: 16px;
  background-color: white;
  
}
</style>
