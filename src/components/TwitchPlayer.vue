<!-- TwitchPlayer.vue -->

<template>
  <div class="twitch-player-container">
    <iframe id="video_embed" :src="getTwitchPlayerSrc" height="100%" width="100%" frameborder="0" scrolling="no"
            style="border: none;" v-show="!getIframeLoading">
    </iframe>
  </div>
</template>

<script setup>
// eslint-disable-next-line no-unused-vars
import { ref, computed } from 'vue'
import { useQuasar } from 'quasar'

const $q = useQuasar()

const getTwitchPlayerSrc = computed(() => {
  return $q.dark.isActive
    ? 'https://player.twitch.tv/?channel=baiano&parent=multistream-ten.vercel.app&darkpopout'
    : 'https://player.twitch.tv/?channel=baiano&parent=multistream-ten.vercel.app'
})
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
