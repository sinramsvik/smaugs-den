<template>
  <section>
    <list-title></list-title>
    <div class="columns is-multiline">
      <background-clients class="column is-2-desktop is-3 is-4" @hover="setProject" v-for="(entry,index) in entries" :key="index" :index="index" :client="entry.fields.client"></background-clients>
        <div v-if="project" class="align">
          <img v-if="project.fields.photo" :src="project.fields.photo[0].url">
        </div>
    </div>
  </section>
</template>

<script>
import BackgroundClients from './BackgroundClients.vue'
import ListTitle from './common/ListTitle.vue'
export default {
  components: { 
    BackgroundClients,
    ListTitle
  },
  data () {
    return {
      entries: null,
      project: null
    }
  },
  created () {
    this.fetchData()
  },

  methods: {
    fetchData() {
      let xhr = new XMLHttpRequest()
      let self = this
      xhr.open('GET','https://api.airtable.com/v0/appudoYlR0W35iwUx/work?api_key=keyNazOMJHA5IFSJw')
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
  @import "../assets/scss/variables.scss";
  img {
    opacity: 0.5;
  }
  .align {
    z-index: -1;
    position: absolute;
    left: 33%;
    width: 520px;
  }
</style>