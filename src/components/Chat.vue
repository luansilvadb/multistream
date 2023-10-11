<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <div class="chat">
    <iframe
      src="https://www.twitch.tv/embed/daniels/chat?parent=multistream-ten.vercel.app"
      frameborder="0"
      allowfullscreen="true"
      scrolling="yes"
      width="100%"
      height="100%"
    ></iframe>
  </div>
</template>

<script>
export default {
  // Adicione opções específicas se necessário
}
</script>

<style scoped>
.chat {
  grid-area: 4 / 2 / 4 / 3;
  width: 100%; /* Largura total em telas menores */
  height: 200%; /* Altura automática para ajustar o conteúdo */
  margin: 0px;

}

/* Estilo para telas menores */
@media screen and (max-width: 768px) {
  .chat {
    grid-area: auto; /* Reverta para fluxo automático na grade */
  }
}
</style>
