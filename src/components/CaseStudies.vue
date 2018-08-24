<template>
  <section class="rows spacer-s spacer-m">
    <div class="row columns is-multiline">
      <div class="column is-12">
        <accordion v-for="(entry,index) in entries" :key="index" :number="entry.fields.number" :client="entry.fields.caseName" :description="entry.fields.description">
          <div class="column is-12 columns is-multiline pad">
            <div class="column is-8-desktop is-10-tablet is-12-mobile">
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
  @import "../assets/scss/variables.scss";

  img {
    margin-top: 42px;
  }
  @media only screen and (min-width: 300px) {
    p {
      font-size: $small-f-size;
    }
  }
  @media only screen and (min-width: 600px) {
    p {
      font-size: $not-large-f-size;
    }
  }
  @media only screen and (min-width: 769px) {
    p {
      font-size: $large-f-size;
    }
  }

</style>
