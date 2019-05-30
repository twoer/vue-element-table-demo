<template>
  <div class="address-cell" :style="{ 'max-Height': config.maxHeight + 'px' }" >
    <div v-if="isTemp" class="temp" :style="{ 'line-height': lineHeight + 'px'}" >
      {{row.address}}
    </div>
    <template v-if="isOverflow">
      <el-tooltip class="item" placement="right" :content="row.address" popper-class="el-tooltip-address">
        <div>
          <div v-if="fixHeight" :style="{ height: fixHeight + 'px' }"></div>
          <div class="content" :style="{'line-height': lineHeight + 'px', '-webkit-line-clamp': lineCount}" >{{row.address}}</div>
          <div v-if="fixHeight" :style="{ height: fixHeight + 'px' }"></div>
        </div>
      </el-tooltip>
    </template>
    <template v-else>
      <div class="content" :style="{ 'line-height': lineHeight + 'px'}" >
        {{row.address}}
      </div>
    </template>
  </div>
</template>

<script>
export default {
  name: 'address-cell',
  data () {
    return {
      lineHeight: 20,
      lineCount: 3,
      fixHeight: 0,
      isOverflow: false,
      isTemp: true
    }
  },
  props: {
    row: {},
    column: {},
    config: {
      maxHeight: 0,
      fontSize: 0
    }
  },
  created () {
  },
  methods: {
    refresh () {
      this.isTemp = true
      this.$nextTick(() => {
        let clientHeight = this.$el.querySelector('.temp').clientHeight
        if (clientHeight > this.config.maxHeight) {
          this.isOverflow = true
        } else {
          this.isOverflow = false
        }
        this.isTemp = false
      })
    }
  },
  mounted () {
    this.refresh()
  },
  watch: {
    config: {
      deep: true,
      handler (n, o) {
        if (!n || !n.maxHeight || !n.fontSize) {
          return
        }
        this.lineHeight = Math.round(n.fontSize * 1.5)
        this.lineCount = Math.floor(n.maxHeight / this.lineHeight)
        this.fixHeight = Math.round((n.maxHeight - this.lineHeight * this.lineCount) / 2)
        this.refresh()
      }
    }
  }
}
</script>

<style >
.address-cell .content
{
  display: -webkit-box;
  -webkit-box-orient: vertical;
  overflow: hidden;
}
.el-tooltip-address
{
  max-width: 400px;
  white-space: normal;
  line-height: 1.4em;
}

</style>
