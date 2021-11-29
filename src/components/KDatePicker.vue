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
      const { _props } = this.$parent;
      const { model } = this.form;
      model[_props.prop] = e;
    },
  },
};
</script>

<style>
</style>