<template>
  <div class="container">
    <div class="jumbotron mt-2">
      <h1 class="display-4">Bem-vindo!</h1>
      <buton class="btn btn-danger" @click="efetuarLogout">Sair</buton>
    </div>
  </div>
</template>

<script>
import { logoutMixin} from '@/mixins'
export default {
  name: 'home',
  mixins: [logoutMixin]
}
</script>
