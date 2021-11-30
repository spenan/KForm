<template>
  <el-checkbox
    :value="value"
    :label="label"
    v-bind="$attrs"
    @input="handleCheckboxInput"
    ><slot
  /></el-checkbox>
</template>

<script>
export default {
  name: "KCheckbox",
  props: {
    value: {
      type: [String, Number, Boolean],
    },
    label: {
      type: [String, Number, Boolean],
    },
  },
  methods: {
    handleCheckboxInput(e) {
      this.$emit("input", e);
    },
  },
};
</script>

<style>
</style>