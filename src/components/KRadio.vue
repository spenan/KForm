<template>
  <el-radio
    :value="value"
    :label="label"
    v-bind="$attrs"
    @input="handleRadioInput"
    ><slot
  /></el-radio>
</template>

<script>
export default {
  name: "KRadio",
  props: {
    value: {
      type: [String, Number, Boolean],
    },
    label: {
      type: [String, Number, Boolean],
    },
  },
  methods: {
    handleRadioInput(e) {
      this.$emit("input", e);
    },
  },
};
</script>

<style>
</style>