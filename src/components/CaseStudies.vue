<template>
  <div @click="toggle">
    <span class="number">{{ number }}</span>
    <h1>{{ client }}</h1>
    <h2>{{ description }}</h2>
  </div>
</template>

<script>
export default {
  props: {
    index: Number,
    number: Number,
    client: String,
    description: String
  },
  data () {
    return {
      open: false
    }
  },
  methods: {
    toggle () {
      this.$emit('click', { index: this.index })
      this.open = true
    }
  }
}
</script>

<style lang="scss" scoped>
  @import "../assets/scss/variables.scss";

  h1 {
    display: inline-block;
    font-size: 26px;
  }
  h2 {
    color: $subtext-gray;
    margin-bottom: 36px;
  }
  .number {
    color: $subtext-gray;
    font-size: 12px;
    margin-top: 5px;
    margin-left: -32px;
    margin-right: 0px;
  }
</style>


