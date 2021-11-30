<template>
  <el-slider
    :value="value"
    v-bind="$attrs"
    @input="handleSliderInput"
  ></el-slider>
</template>

<script>
export default {
  name: "KSlider",
  props: {
    value: {
      type: Number,
    },
  },
  methods: {
    handleSliderInput(e) {
      this.$emit("input", e);
    },
  },
};
</script>

<style>
</style>