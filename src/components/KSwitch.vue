<template>
  <el-switch
    :value="value"
    v-bind="$attrs"
    @input="handelSwitchInput"
  ></el-switch>
</template>

<script>
export default {
  name: "KSwitch",
  props: {
    value: {
      type: Boolean,
    },
  },
  data() {
    return {};
  },
  methods: {
    handelSwitchInput(e) {
      this.$emit("input", e);
    },
  },
};
</script>

<style>
</style>