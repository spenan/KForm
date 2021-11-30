<template>
  <el-select :value="value" @input="handleSelectInput" v-bind="$attrs">
    <slot></slot>
    <!-- <el-option label="区域一" value="shanghai"></el-option> -->
  </el-select>
</template>

<script>
export default {
  name: "KSelect",
  data() {
    return {};
  },
  inheritAttrs: false,
  props: {
    value: {
      type: String,
    },
  },
  inject: ["form"],
  methods: {
    handleSelectInput(e) {
      this.$emit('input',e)
    },
  },
};
</script>

<style>
</style>