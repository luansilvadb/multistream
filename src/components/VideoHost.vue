<template>
  <div class="videohost">
    <q-video
      :ratio="16/9"
      src="https://player.twitch.tv/?channel=daniels&parent=multistream-ten.vercel.app&muted=true" frameborder="0" allowfullscreen="true" scrolling="no" height="378" width="620"
    />
    <iframe class="chat"
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
