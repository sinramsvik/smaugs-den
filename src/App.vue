<template>
  <div id="app" class="margins">
    <desktop-header></desktop-header>
    <case-studies></case-studies>
    <about></about>
    <background-list></background-list>
  </div>
</template>

<script>
import DesktopHeader from './components/DesktopHeader.vue'
import CaseStudies from './components/CaseStudies.vue'
import About from './components/About.vue'
import BackgroundList from './components/BackgroundList.vue'
export default {
  name: 'app',
  components: {
    DesktopHeader,
    CaseStudies,
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
      margin: 32px;
    }
  @media only screen and (min-width: 769px) {
    .margins {
      margin: 3% 6%;
    }
  }
</style>

