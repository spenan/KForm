<template>
  <el-select :value="value" @change="handleChange" v-bind="$attrs">
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
    handleChange(e) {
      const { _props } = this.$parent;
      const { model } = this.form;
      model[_props.prop] = e;
    },
  },
};
</script>

<style>
</style>