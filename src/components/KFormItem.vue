<template>
  <div>
    <el-form-item :label="label" :prop="prop">
      <slot></slot>
    </el-form-item>
  </div>
</template>

<script>
export default {
  name: "KFormItem",
  props: {
    label: {
      type: String,
    },
    prop: {
      type: String,
    },
  }
};
</script>

<style>
</style>