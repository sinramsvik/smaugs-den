<template>
  <section class="rows spacer">
    <div class="row columns is-multiline">
      <div class="column is-12">
        <accordion v-for="(entry,index) in entries" :key="index" :number="entry.fields.number" :client="entry.fields.caseName" :description="entry.fields.description">
          <div class="column is-12 columns is-multiline">
            <div class="column is-8">
              <p>{{ entry.fields.caseText }}</p>
              <p>{{ entry.fields.caseTextTwo }}</p>
            </div>
            <div class="column is-12" v-for="(photos,index) in entry.fields.photo" :key="index">
              <img :src="photos.url" />
            </div>
          </div>
        </accordion>
      </div>
    </div>
  </section>
</template>

<script>
import Accordion from './Accordion.vue'
export default {
  components: { Accordion },
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
      xhr.open('GET','https://api.airtable.com/v0/appudoYlR0W35iwUx/casestudies?api_key=keyNazOMJHA5IFSJw')
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

  img {
    margin-top: 42px;
  }
  p {
    font-size: 22px;
    margin-bottom: 26px;
  }
</style>
