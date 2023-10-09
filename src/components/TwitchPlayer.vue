<template>
  <div class="twitch-player-container">
    <div v-if="getIframeLoading" class="spinner-container">
      <q-spinner :color="$q.dark.isActive ? 'white' : 'primary'" size="7em" />
    </div>
    <iframe id="video_embed" :src="getTwitchPlayerSrc" frameborder="0" scrolling="no"
            style="border: none;" @load="iframeLoaded" v-show="!getIframeLoading">
    </iframe>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import { useQuasar } from 'quasar'

const iframeLoadingDark = ref(true)
const iframeLoadingLight = ref(true)
const iframeLoadingTheme = ref('dark') // Padrão para o tema escuro
const $q = useQuasar()

const getIframeLoading = computed(() => {
  return iframeLoadingTheme.value === 'dark' ? iframeLoadingDark.value : iframeLoadingLight.value
})

const getTwitchPlayerSrc = computed(() => {
  return $q.dark.isActive
    ? 'https://player.twitch.tv/?channel=baiano&parent=stream.luansilva.com.br&darkpopout'
    : 'https://player.twitch.tv/?channel=baiano&parent=stream.luansilva.com.br'
})

const iframeLoaded = () => {
  if (iframeLoadingTheme.value === 'dark') {
    iframeLoadingDark.value = false
  } else {
    iframeLoadingLight.value = false
  }
}

</script>

<style scoped>
.twitch-player-container {
  position: relative;
  width: 100%;
  padding-bottom: 56.25%; /* 16:9 aspect ratio - adjust as needed */
  overflow: hidden;
}

.spinner-container {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.twitch-player-container iframe {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}
</style>
