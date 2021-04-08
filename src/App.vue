<template>
  <Header/>
  <Jobs/>
</template>

<script>
import Jobs from './components/Jobs.vue'
import Header from './components/Header.vue'

export default {
  name: 'App',
  components: {
    Jobs,
    Header
  }
}
</script>
<style>
@import "../dist/style.css"
</style>
