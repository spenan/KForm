<template>
  <el-form
    :model="model"
    :rules="rules"
    :labelPosition="labelPosition"
    :labelWidth="labelWidth"
    :showMessage="showMessage"
    ref="form"
  >
    <slot></slot>
  </el-form>
</template>

<script>
export default {
  name: "KForm",
  props: {
    model: {
      type: Object,
      required: true,
    },
    rules: {
      type: Object,
    },
    labelPosition: {
      type: String,
      default: "right",
    },
    showMessage: {
      type: Boolean,
      default: true,
    },
    labelWidth: {
      type: String,
    },
  },
  provide() {
    return {
      form: this,
    };
  },
  methods: {
    validate(fn) {
      this.$refs.form.validate((valid, errInfo) => {
        fn(valid, errInfo);
      });
    },
  },
};
</script>

<style>
</style>