<template>
  <section class="rows columns is-multiline">
    <div class="row column is-8" v-for="(entry,index) in entries" :key="index">
      <h2 class="headfont">{{ entry.fields.header }}</h2>
      <p class="row aboutfont">{{ entry.fields.about }}</p>
      <p class="row aboutfont">{{ entry.fields.aboutAlt }}</p>
    </div>
    <div class="column is-12 space"></div>
  </section>
</template>

<script>
export default {
  data () {
    return {
      entries: null
    }
  },

  watch: {
    currentPage: 'fetchData'
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
@import "../assets/scss/variables.scss";

.space {
  height: 144px;
}

</style>