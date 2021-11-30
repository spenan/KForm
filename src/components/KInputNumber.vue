<template>
  <el-input-number
    :value="value"
    @input="handleInput"
    @change="handleInput"
    v-bind="$attrs"
  ></el-input-number>
</template>

<script>
export default {
  name: "KInputNumber",
  props: {
    value: {
      type: Number,
    },
  },
  methods: {
    handleInput(e) {
      this.$emit("input", e);
    },
  },
};
</script>

<style>
</style>