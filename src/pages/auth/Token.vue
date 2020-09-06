<template>
  <h1>Login</h1>
</template>

<script>
import axios from '@/http'
export default {
  name: 'Token',
  mounted() {
    this.$store.commit('login', this.$route.params.token)
    axios
      .get('/auth/info')
      .then(() => {
        this.$router.push("/songs")
      })
  }
}
</script>