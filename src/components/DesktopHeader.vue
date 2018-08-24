<template>
  <header class="spacer-s">
    <div class="columns is-mobile" v-for="(entry,index) in entries" :key="index">
      <div class="column is-9-desktop is-6-tablet">
        <h2>{{ entry.fields.aboutAltTwo }}</h2>
      </div>
      <social class="column"></social>
    </div>
  </header>
</template>

<script>
import Social from './Social.vue'
export default {
  components: { Social },
  data () {
    return {
      entries: null
    }
  },
  created () {
    this.fetchData()
  },

  methods: {
    fetchData() {
      let xhr = new XMLHttpRequest()
      let self = this
      xhr.open('GET','https://api.airtable.com/v0/appudoYlR0W35iwUx/header?api_key=keyNazOMJHA5IFSJw')
      xhr.onload = function () {
        let response = JSON.parse(xhr.responseText)
        self.entries = response.records
      }
      xhr.send()
    },
  }
}
</script>

<style lang="scss" scoped>
  @import "../assets/scss/variables.scss";

  h2 {
    font-size: 12px;
    margin-top: 5px;
  }
  .marginbottom {
    margin-bottom: 58px;
  }
</style>

