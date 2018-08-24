<template>
  <section class="is-hidden-mobile">
    <list-title></list-title>
    <div class="columns is-multiline is-mobile">
      <background-clients class="column is-2-desktop is-3-tablet" @hover="setProject" v-for="(entry,index) in entries" :key="index" :index="index" :client="entry.fields.client"></background-clients>
        <div class="back-img" v-if="project">
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
  .back-img {
    z-index: -1;
    position: absolute;
  }
  @media only screen and (min-width: 300px) {
    .back-img {
      left: 10%;
      width: 80%;
    }
  }
  @media only screen and (min-width: 769px) {
    .back-img {
      left: 15%;
      width: 66%;
    }
  } 
  @media only screen and (min-width: 1024px) {
    .back-img {
      left: 25%;
      width: 50%;
    }
  }
  @media only screen and (min-width: 1216px) {
    .back-img {
      left: 33%;
      width: 33%;
    }
  }
</style>