<template>
  <div @click="open = !open">
    <span class="number">{{ number }}</span>
    <h1>{{ client }}</h1>
    <h2>{{ description }}</h2>
    <div v-if="open">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    number: Number,
    client: String,
    description: String
  },
  data () {
    return {
      open: false
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
  @media only screen and (min-width: 300px) {
    h2 {
      color: $subtext-gray;
      font-size: 12px;
      white-space: normal;
      margin-bottom: 36px;
    }
  }
  @media only screen and (min-width: 769px) {
    h2 {
      margin-bottom: 36px;
      font-size: 100%;
    }
  }
  .number {
    color: $subtext-gray;
    font-size: 12px;
    margin-top: 5px;
    margin-left: -32px;
    margin-right: 0px;
  }
</style>


