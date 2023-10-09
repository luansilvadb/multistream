<!-- TwitchPlayer.vue -->

<template>
  <div class="twitch-player-container">
    <iframe
      id="twitchPlayer"
      :src="getTwitchPlayerSrc"
      height="100%"
      width="100%"
      frameborder="0"
      scrolling="no"
      style="border: none;"
    ></iframe>
  </div>
</template>

<script setup>
// eslint-disable-next-line no-unused-vars
import { ref, computed } from 'vue'
import { useQuasar } from 'quasar'

const $q = useQuasar()

const getTwitchPlayerSrc = computed(() => {
  return $q.dark.isActive
    ? 'https://player.twitch.tv/?channel=baiano&parent=stream.luansilva.com.br&darkpopout'
    : 'https://player.twitch.tv/?channel=baiano&parent=stream.luansilva.com.br'
})
</script>

<style scoped>
.twitch-player-container {
  height: 100%;
  width: 100%;
}
</style>
