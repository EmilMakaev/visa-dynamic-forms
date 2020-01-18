<template>
  <div id="app">
    <MainComponent />
  </div>
</template>

<script>
import MainComponent from './components/MainComponent.vue'

export default {
  name: 'app',
  components: {
    MainComponent
  }
}
</script>

<style lang="scss">
@import '@/styles/global.scss';
</style>
