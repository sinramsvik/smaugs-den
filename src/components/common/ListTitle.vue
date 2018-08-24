<template>
  <div>
    <div v-for="(entry,index) in entries" :key="index">
      <p class="aboutalt">{{ entry.fields.aboutAlt }}</p>
    </div>
  </div>
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
      xhr.open('GET','https://api.airtable.com/v0/appudoYlR0W35iwUx/header?api_key=keyNazOMJHA5IFSJw')
      xhr.onload = function () {
        let response = JSON.parse(xhr.responseText)
        self.entries = response.records
      }
      xhr.send()
    }
  }
}
</script>

<style lang="scss" scoped>

  .aboutalt {
    font-size: 12px;
    margin-bottom: 36px;
  }

</style>

