<template>
  <section class="spacer-s spacer-m">
    <div class="rows columns is-multiline">
      <div class="row column is-8-desktop is-10-tablet is-12-mobile" v-for="(entry,index) in entries" :key="index">
        <h2 class="headfont">{{ entry.fields.header }}</h2>
        <p class="row text-mobile text-desktop">{{ entry.fields.about }}</p>
        <p class="row text-mobile text-desktop">{{ entry.fields.aboutAlt }}</p>
      </div>
    </div>
  </section>  
</template>

<script>
export default {
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
      xhr.open('GET','https://api.airtable.com/v0/appudoYlR0W35iwUx/aboutshort?api_key=keyNazOMJHA5IFSJw')
      xhr.onload = function () {
        let response = JSON.parse(xhr.responseText)
        self.entries = response.records
      }
      xhr.send()
    }
  }
}
</script>

<style lang="scss">

</style>