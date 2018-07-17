<template>
  <div class="scrollbar">
    <div class="simplebar-track vertical" v-show="vertical">
      <div class="simplebar-scrollbar"></div>
    </div>
    <div class="simplebar-track horizontal" v-show="horizontal">
      <div class="simplebar-scrollbar"></div>
    </div>
    <div class="simplebar-scroll-content">
      <div class="simplebar-content">
        <slot />
      </div>
    </div>
  </div>
</template>

<script>
import SimpleBar from 'simplebar'

export default {
  props: {
    setTop: {
      type: [String, Number, Boolean],
      default: 0,
    },
    recalculate: {
      type: [String, Number, Boolean],
      default: 0,
    },
    vertical: {
      type: Boolean,
      default: true,
    },
    horizontal: {
      type: Boolean,
      default: false,
    },
  },
  data() {
    return {
      scrollbar: false,
    }
  },
  watch: {
    recalculate(v) {
      var vm = this
      vm.doRecalculate()
    },
    setTop(v) {
      if (v != undefined) {
        this.scrollToTop(v)
      }
    },
  },
  mounted() {
    this.init()
  },
  destroy() {
    if (this.scrollbar !== false) {
      this.scrollbar.unMount()
    }
  },
  methods: {
    scrollToTop(pos) {
      pos = typeof pos == "boolean" ? 0 : parseInt(pos)

      if (this.scrollbar !== false) {
        this.scrollbar.getScrollElement().scrollTop = pos
      }
    },

    doRecalculate() {
      if (this.scrollbar !== false) {
        this.scrollbar.recalculate()
      }
    },

    init() {
      if (this.scrollbar === false) {
        this.scrollbar = new SimpleBar(this.$el, {
          autoHide: false
        })
      }
    },
  },
}
</script>
