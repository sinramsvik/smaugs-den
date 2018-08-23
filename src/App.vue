<template>
  <div id="app" class="margins">
    <desktop-header></desktop-header>
    <cases class="spacer"></cases>
    <about></about>
    <background-list></background-list>
  </div>
</template>

<script>
import DesktopHeader from './components/DesktopHeader.vue'
import Cases from './components/Cases.vue'
import About from './components/About.vue'
import BackgroundList from './components/BackgroundList.vue'
export default {
  name: 'app',
  components: {
    DesktopHeader,
    Cases,
    About,
    BackgroundList
  },
  data () {
    return {

    }
  }
}
</script>

<style lang="scss">
  @import '/assets/scss/app';

  .margins {
    margin: 55px 80px;
  }
  .spacer {
    margin-bottom: 144px;
  }
</style>

