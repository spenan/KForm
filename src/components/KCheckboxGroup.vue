<template>
  <el-checkbox-group
    :value="value"
    v-bind="$attrs"
    @input="handleCheckboxGroup"
  >
    <slot />
  </el-checkbox-group>
</template>

<script>
export default {
  name: "KCheckboxGroup",
  props: {
    value: {
      type: Array,
    },
  },
  methods: {
    handleCheckboxGroup(e) {
      this.$emit("input", e);
    },
  },
};
</script>

<style>
</style>