<template>
  <el-date-picker
    v-model="currentValue"
    :type="type"
    :range-separator="rangeSeparator"
    unlink-panels
    :start-placeholder="placeholder[0]"
    :end-placeholder="placeholder[1]"
    :value-format="valueFormat"
    :style="{width: width + 'px'}"
    @change="onChange"
  />
</template>

<script>
export default {
  name: 'DateRange',
  props: {
    value: {
      type: [String, Array],
      default: ''
    },
    // 宽度
    width: {
      type: [String, Number],
      default: 240
    },
    // 日期类型
    type: {
      type: String,
      default: 'daterange'
    },
    // 日期格式
    valueFormat: {
      type: String,
      default: 'yyyy-MM-dd'
    },
    // 分隔符
    rangeSeparator: {
      type: String,
      default: '至'
    },
    // placeholder
    placeholder: {
      type: Array,
      default: () => ['开始日期', '结束日期']
    }
  },
  data() {
    return {
    }
  },
  computed: {
    currentValue: {
      get() {
        return this.value
      },
      set(val) {
        this.$emit('input', val)
      }
    }
  },
  methods: {
    onChange(val) {
      this.$emit('change', val)
    }
  }
}
</script>

<style scoped>

</style>
