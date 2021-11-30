<template>
  <el-time-select :value="value" v-bind="$attrs" @input="handleTimeSelect">
  </el-time-select>
</template>

<script>
export default {
  name: "KTimePicker",
  props: {
    value: {
      type: [Date, String],
    },
  },
  methods: {
    handleTimeSelect(e) {
      this.$emit("input", e);
    },
  },
};
</script>

<style>
</style>