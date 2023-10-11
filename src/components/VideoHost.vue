<template>
  <div class="videohost">
    <iframe :src="getVideoSrc" height="100%" width="100%" frameborder="0" scrolling="no"
            style="border: none;" v-show="!getIframeLoading">
          </iframe>
          <iframe frameborder="0" scrolling="no" id="chat_embed" :src="getChatSrc" @load="iframeLoaded" height="100%"
            width="100%" style="border: none;" v-show="!getIframeLoading">
          </iframe>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import { useQuasar } from 'quasar'

// const rightDrawerOpen = ref(false)
const iframeLoadingDark = ref(true)
const iframeLoadingLight = ref(true)
const iframeLoadingTheme = ref('dark') // Padrão para o tema escuro
const $q = useQuasar()

const getIframeLoading = computed(() => {
  return iframeLoadingTheme.value === 'dark' ? iframeLoadingDark.value : iframeLoadingLight.value
})

const getVideoSrc = computed(() => {
  return $q.dark.isActive
    ? 'https://player.twitch.tv/?channel=daniels&parent=multistream-ten.vercel.app&darkpopout'
    : 'https://player.twitch.tv/?channel=daniels&parent=multistream-ten.vercel.app'
})

const getChatSrc = computed(() => {
  return $q.dark.isActive
    ? 'https://www.twitch.tv/embed/daniels/chat?parent=multistream-ten.vercel.app&darkpopout'
    : 'https://www.twitch.tv/embed/daniels/chat?parent=multistream-ten.vercel.app'
})

const iframeLoaded = () => {
  if (iframeLoadingTheme.value === 'dark') {
    iframeLoadingDark.value = false
  } else {
    iframeLoadingLight.value = false
  }
}

// eslint-disable-next-line no-unused-vars
const isMobile = computed(() => {
  return $q.screen.width <= 500 // Defina o valor conforme necessário
})
</script>

<style scoped>
.videohost {
  grid-area: 2 / 2 / 4 / 3;
  width: 100%; /* Largura total em telas menores */
  height: auto; /* Altura automática para ajustar o conteúdo */
  margin: 0;
}
.chat{
max-height: 490px;
}

/* Estilo para telas menores */
@media screen and (max-width: 768px) {
  .videohost {
    grid-area: auto; /* Reverta para fluxo automático na grade */
  }
}
</style>
