<template>
  <div class="row">
    <QRCodeVue3
      :width="size"
      :height="size"
      :value="wifiValue"
      :key="wifiValue + size"
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
      :download="false"
      myclass="my-qur"
      imgclass="img-qr"
      downloadButton="my-button"
      :downloadOptions="{ name: 'vqr', extension: 'png' }"
    />
  </div>
  <div>
    <q-input v-model="mynetwork" label="SSID" />
    <q-input v-model="password" label="PASSWORD" />

    <q-slider
      class="q-mt-lg"
      v-model="size"
      :min="100"
      :max="500"
      :step="4"
      label
      :label-value="'QRCode Size: ' + size + 'px'"
      label-always
      color="purple"
    />

    <div class="q-pa-md">
      <div class="q-gutter-sm">
        <q-radio v-model="AuthenticationType" val="WEP" label="WEP" />
        <q-radio v-model="AuthenticationType" val="WPA" label="WPA" />
        <q-radio v-model="AuthenticationType" val="WPA2-EAP" label="WPA2-EAP" />
        <q-radio v-model="AuthenticationType" val="nopass" label="パスワードなし" />
      </div>
    </div>

    <div class="q-pa-md">
      <div class="q-gutter-sm">
        <div>
          <q-checkbox v-model="TransitionMode" label="WPA2/WPA3 トランジションモード無効" />
        </div> 
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
  import { ref, computed, defineModel } from 'vue';
  import QRCodeVue3 from "qrcode-vue3";

  const mynetwork = ref('mynetwork');
  const password = ref('password');

  const size = ref(200);
  const AuthenticationType = ref('WEP');
  const TransitionMode = ref(false);

  // WiFi用QRCodeテキスト生成
  const wifiValue = computed(() => {
    return('WIFI:' 
     + 'S:"' + mynetwork.value + '"'
     + ';T:' + AuthenticationType.value
     + ';R:' + (TransitionMode.value === false ? '0' : '1')
     + ';P:"' + password.value + '"'
     + ';;')
  });
</script>