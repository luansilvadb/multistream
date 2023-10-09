<!-- TwitchPlayer.vue -->
<template>
  <div class="twitch-player-container">
    <div v-if="shouldShowSpinner" class="spinner-container">
      <q-spinner :color="$q.dark.isActive ? 'white' : 'primary'" size="7em" />
    </div>
    <iframe id="video_embed" :src="getTwitchPlayerSrc" frameborder="0" scrolling="no"
            style="border: none;" @load="iframeLoaded" v-show="!iframeLoading">
    </iframe>
  </div>
</template>

<script setup>
import { ref, computed, watch } from 'vue'
import { useQuasar } from 'quasar'

const props = defineProps(['currentTheme', 'rightDrawerOpen'])

const iframeLoading = ref(true)
const $q = useQuasar()

const shouldShowSpinner = computed(() => {
  return iframeLoading.value && props.rightDrawerOpen
})

const getTwitchPlayerSrc = computed(() => {
  return props.currentTheme
    ? 'https://player.twitch.tv/?channel=baiano&parent=multistream-ten.vercel.app&darkpopout'
    : 'https://player.twitch.tv/?channel=baiano&parent=multistream-ten.vercel.app'
})

watch(
  () => props.rightDrawerOpen,
  (newRightDrawerOpen) => {
    console.log('Right Drawer Open:', newRightDrawerOpen)
    // Additional logic as needed
  }
)

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
