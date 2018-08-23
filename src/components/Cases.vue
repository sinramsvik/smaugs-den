<template>
  <section class="rows spacer">
    <div class="row columns is-multiline">
      <div class="column is-8">
        <case-studies @click="setProject" v-for="(entry,index) in entries" :key="index" :index="index" :number="entry.fields.number" :client="entry.fields.caseName" :description="entry.fields.description"></case-studies>
      </div>
      <div class="column is-12 columns is-multiline" v-if="project">
        <div class="column is-8">
          <p>{{ project.fields.caseText }}</p>
          <p>{{ project.fields.caseTextTwo }}</p>
        </div>
        <div class="column is-12" v-for="(photos,index) in project.fields.photo" :key="index">
          <img :src="photos.url" />
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import CaseStudies from './CaseStudies.vue'
export default {
  components: { CaseStudies },
  data () {
    return {
      entries: null,
      project: null
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
      xhr.open('GET','https://api.airtable.com/v0/appudoYlR0W35iwUx/casestudies?api_key=keyNazOMJHA5IFSJw')
      xhr.onload = function () {
        let response = JSON.parse(xhr.responseText)
        self.entries = response.records
      }
      xhr.send()
    },
    setProject ({ index }) {
      let item = this.entries[index]
      this.project = item
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
