<template>
  <el-rate :value="value" v-bind="$attrs" @input="handleRateInput"> </el-rate>
</template>

<script>
export default {
  name: "KRate",
  props: {
    value: {
      type: Number,
    },
  },
  inject: ["form"],
  methods: {
    handleRateInput(e) {
      this.$emit("input", e);
    },
  },
};
</script>

<style>
</style>