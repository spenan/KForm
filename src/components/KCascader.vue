<template>
  <el-cascader
    :value="value"
    :options="options"
    v-bind="$attrs"
    @input="handleCascader"
  ></el-cascader>
</template>

<script>
export default {
  name: "KCascader",
  props: {
    value: {
      type: [String, Number, Boolean, Object, Array, null, undefined, Symbol],
    },
    options: {
      type: Array,
    },
  },
  methods: {
    handleCascader(e) {
      this.$emit("input", e);
    },
  },
};
</script>

<style>
</style>