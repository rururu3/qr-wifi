<template>
  <qrcode-vue :value="wifiValue" :level="level" :render-as="renderAs" :size="size" />
</template>

<script setup lang="ts">
  import { ref, computed } from 'vue'
  import QrcodeVue, { type Level, type RenderAs } from 'qrcode.vue'

  const mynetwork = ref('mynetwork')
  const password = ref('password')
  const level = ref<Level>('H')
  const renderAs = ref<RenderAs>('canvas')
  const size = ref(200)

  // WiFi用QRCodeテキスト生成
  const wifiValue = computed(() => {
    return('WIFI:S:"' + mynetwork.value + '";T:WPA;P:"' + password.value + '";;')
  });
</script>