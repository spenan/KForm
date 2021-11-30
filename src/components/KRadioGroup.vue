<template>
  <el-radio-group :value="value" v-bind="$attrs" @input="handleRadioGroupInput">
    <slot />
  </el-radio-group>
</template>

<script>
export default {
  name: "KRadioGroup",
  props: {
    value: {
      type: [String, Number, Boolean],
    },
  },
  methods: {
    handleRadioGroupInput(e) {
      this.$emit("input", e);
    },
  },
};
</script>

<style>
</style>