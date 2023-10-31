<template>
  <q-page class="q-pa-lg">
    <div class="q-gutter-md">
      <h4 class="text-h6 q-mb-md">Bem-vindo à nossa Central de Ajuda</h4>
      <p>
        Aqui você encontrará informações valiosas para aproveitar ao máximo nossa aplicação.
      </p>

      <div class="q-mb-md">
        <h5 class="text-h6">Como Começar</h5>
        <ol>
          <li>Registre-se na nossa plataforma.</li>
          <li>Faça login na sua conta.</li>
          <li>Explore todas as funcionalidades da aplicação.</li>
        </ol>
      </div>

      <div>
        <h5 class="text-h6">Perguntas Frequentes</h5>
        <ul>
          <li>Como redefinir minha senha?</li>
          <li>Como entrar em contato com o suporte?</li>
          <li>Como personalizar as configurações da minha conta?</li>
        </ul>
      </div>
    </div>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'HelpPage'
})
</script>


