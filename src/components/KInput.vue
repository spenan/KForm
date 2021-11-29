<template>
  <el-input
    :type="type"
    :value="value"
    @input="handleInput"
    v-bind="$attrs"
  ></el-input>
</template>

<script>
export default {
  name: "KInput",
  data() {
    return {};
  },
  inheritAttrs: false,
  props: {
    type: {
      type: String,
      default: "text",
    },
    value: {
      type: String,
    },
  },
  methods: {
    handleInput(e) {
      this.$emit("input", e);
    },
  }
};
</script>

<style>
</style>