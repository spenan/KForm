<template>
  <el-date-picker
    :value="value"
    :type="type"
    v-bind="$attrs"
    @input="handleDatePicker"
  >
  </el-date-picker>
</template>

<script>
export default {
  name: "KDatePicker",
  data() {
    return {};
  },
  inheritAttrs: false,
  props: {
    value: {
      type: String,
    },
    type: {
      type: String,
      default: "date",
    },
  },
  inject: ["form"],
  methods: {
    handleDatePicker(e) {
      this.$emit('input',e)
    },
  },
};
</script>

<style>
</style>