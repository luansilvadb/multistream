<template>
  <div class="container">
    <VideoPrincipal />
    <VideoHost />
    <Chat />
  </div>
</template>

<script>
import VideoPrincipal from './VideoPrincipal.vue'
import VideoHost from './VideoHost.vue'
import Chat from './Chat.vue'

export default {
  components: {
    VideoPrincipal,
    VideoHost,
    Chat
  }
}
</script>

<style scoped>
.container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: auto 1.2fr 1.2fr; /* Ajustei a primeira linha para 'auto' */
  gap: 0px 0px;
  grid-auto-flow: row;
}

/* Estilo para telas menores (por exemplo, dispositivos móveis) */
@media screen and (max-width: 768px) {
  .container {
    grid-template-columns: 1fr;
    grid-template-rows: auto; /* Altura automática */
  }

  .videoprincipal,
  .videohost,
  .navbar,
  .chat {
    width: 100%; /* Largura total para ocupar a largura da tela */
  }
}
</style>
