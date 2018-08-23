<template>
  <div>
    <p class="client" @mouseover="toggle">{{ client }}</p>
  </div>
</template>

<script>
export default {
  props: {
    index: Number,
    client: String
  },
  data () {
    return {
      open: false
    }
  },
  methods: {
    toggle () {
      this.$emit('hover', { index: this.index })
      this.open = true
    }
  }
}
</script>

<style lang="scss" scoped>
  p.client {
    z-index: 10;
    font-size: 12px;
    &:hover {
      background-color: #eaeaea;
      border-radius: 4px;
    }
  }
</style>