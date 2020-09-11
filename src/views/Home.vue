<template>
  <div class="home">
    <Acceuil />
  </div>
</template>

<script>
// @ is an alias to /src
import Acceuil from '@/components/Acceuil.vue'

export default {
  name: 'Home',
  components: {
    Acceuil
  }
}
</script>
<style lang="scss" scoped>
.home {
  height: 100vh;
}
</style>
