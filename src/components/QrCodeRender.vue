<template>
  <QRCodeVue3
    :width="size"
    :height="size"
    :value="wifiValue"
    :qrOptions="{ typeNumber: 0, mode: 'Byte', errorCorrectionLevel: 'H' }"
    :imageOptions="{ hideBackgroundDots: true, imageSize: 0.4, margin: 0 }"
    :dotsOptions="{
      type: 'dots',
      color: '#26249a',
      gradient: {
        type: 'linear',
        rotation: 0,
        colorStops: [
          { offset: 0, color: '#26249a' },
          { offset: 1, color: '#26249a' },
        ],
      },
    }"
    :backgroundOptions="{ color: '#ffffff' }"
    :cornersSquareOptions="{ type: 'dot', color: '#000000' }"
    :cornersDotOptions="{ type: undefined, color: '#000000' }"
    fileExt="png"
    :download="true"
    myclass="my-qur"
    imgclass="img-qr"
    downloadButton="my-button"
    :downloadOptions="{ name: 'vqr', extension: 'png' }"
  />
</template>

<script setup lang="ts">
  import { ref, computed } from 'vue';
  import QRCodeVue3 from "qrcode-vue3";

  const mynetwork = ref('mynetwork');
  const password = ref('password');

  const size = ref(200);

  // WiFi用QRCodeテキスト生成
  const wifiValue = computed(() => {
    return('WIFI:S:"' + mynetwork.value + '";T:WPA;P:"' + password.value + '";;')
  });
</script>