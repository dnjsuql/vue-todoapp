<template>
  <div id="app">
    <Header />
    <Contents />
  </div>
</template>

<script>
import '@/assets/scss/style.scss'
import Contents from '@/views/Contents.vue'
import Header from '@/views/common/Header.vue'

export default {
  name: 'App',
  components: {
    Header,
    Contents,
  },
}
</script>

<style lang="scss">
#app {
  margin: 0 auto;
  max-width: 360px;
  width: 100%;
  min-height: 100vh;
  height: 100vh;
  display: flex;
  flex-direction: column;
}
</style>
