<template>
  <div class="twitch-player-container">
    <q-spinner v-if="getIframeLoading" :color="$q.dark.isActive ? 'white' : 'primary'" size="7em" />
    <iframe id="video_embed" :src="getTwitchPlayerSrc" height="100%" width="100%" frameborder="0" scrolling="no"
            style="border: none;" @load="iframeLoaded">
    </iframe>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import { useQuasar } from 'quasar'

const $q = useQuasar()
const iframeLoading = ref(true)

const getTwitchPlayerSrc = computed(() => {
  return $q.dark.isActive
    ? 'https://player.twitch.tv/?channel=baiano&parent=multistream-ten.vercel.app&darkpopout'
    : 'https://player.twitch.tv/?channel=baiano&parent=multistream-ten.vercel.app'
})

const getIframeLoading = computed(() => iframeLoading.value)

const iframeLoaded = () => {
  iframeLoading.value = false
}

</script>

<style scoped>
.twitch-player-container {
  position: relative;
  width: 100%;
  padding-bottom: 56.25%; /* 16:9 aspect ratio - adjust as needed */
  overflow: hidden;
}

.twitch-player-container iframe {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}
</style>
