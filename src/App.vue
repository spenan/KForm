<template>
  <div id="app">
    <Carousel/>
    <KForm
      :model="formData"
      ref="kform"
      :rules="rules"
      label-position="top"
      label-width="80px"
      :show-message="false"
    >
      <KFormItem label="用户" prop="UserName">
        <KInput
          type="text"
          v-model="formData.UserName"
          placeholder="请输入用户信息"
        />
      </KFormItem>
      <KFormItem label="密码" prop="PassWord">
        <KInput
          type="password"
          v-model="formData.PassWord"
          placeholder="请输入密码"
        />
      </KFormItem>
      <KFormItem label="备注">
        <KInput
          type="text"
          v-model="formData.Remake"
          placeholder="请输入备注"
        />
      </KFormItem>
      <KFormItem label="活动区域" prop="Region">
        <KSelect
          v-model="formData.Region"
          style="width: 100%"
          placeholder="请选择活动区域"
        >
          <KOption label="上海" value="shanghai" />
          <KOption label="广州" value="guangzhou" />
        </KSelect>
      </KFormItem>
      <KFormItem label="活动日期">
        <KDatePicker
          v-model="formData.ActionDay"
          style="width: 100%"
          placeholder="请选择活动日期"
          unlink-panels
          :picker-options="pickerOptions"
          value-format="yyyy-MM-dd"
        />
      </KFormItem>

       <KFormItem label="活动时间">
        <KTimePicker
          v-model="formData.ActionTime"
          style="width: 100%"
          placeholder="请选择活动时间"
        />
      </KFormItem>

      <KFormItem label="活动人数">
        <KInputNumber style="width: 100%" v-model="formData.Counter" />
      </KFormItem>

      <KFormItem label="活动满意度">
        <KRate v-model="formData.Rate" />
      </KFormItem>

      <KFormItem label="活动价格">
        <KSlider v-model="formData.Price" />
      </KFormItem>

      <KFormItem label="是否配送">
        <KSwitch v-model="formData.IsSend" />
      </KFormItem>

      <el-button type="primary" @click="submitForm('kform')">提交</el-button>
      <el-button @click="resetForm('kform')">重置</el-button>
    </KForm>
  </div>
</template>

<script>
import Carousel from './Carousel.vue'
import KForm from "./components/KForm.vue";
import KFormItem from "./components/KFormItem.vue";
import KInput from "./components/KInput.vue";
import KInputNumber from "./components/KInputNumber.vue";
import KSelect from "./components/KSelect.vue";
import KOption from "./components/KOption";
import KDatePicker from "./components/KDatePicker";
import KTimePicker from './components/KTimePicker'
import KRate from "./components/KRate";
import KSlider from "./components/KSlider";
import KSwitch from './components/KSwitch'
export default {
  name: "App",
  components: {
    Carousel,
    KForm,
    KFormItem,
    KInput,
    KSelect,
    KOption,
    KInputNumber,
    KTimePicker,
    KRate,
    KSlider,
    KDatePicker,
    KSwitch
  },
  data() {
    return {
      formData: {
        UserName: "",
        PassWord: "",
        ActionDay:'',
        ActionTime: "",
        Region: "",
        Counter: 0,
      },
      rules: {
        UserName: [
          { required: true, message: "请输入用户信息", trigger: "blur" },
        ],
        PassWord: [{ required: true, message: "请输入密码", trigger: "blur" }],
        Region: [
          { required: true, message: "请选择活动区域", trigger: "change" },
        ],
      },
      pickerOptions: {
        disabledDate(time) {
          return time.getTime() > Date.now();
        },
        shortcuts: [
          {
            text: "今天",
            onClick(picker) {
              picker.$emit("pick", new Date());
            },
          },
          {
            text: "昨天",
            onClick(picker) {
              const date = new Date();
              date.setTime(date.getTime() - 3600 * 1000 * 24);
              picker.$emit("pick", date);
            },
          },
          {
            text: "一周前",
            onClick(picker) {
              const date = new Date();
              date.setTime(date.getTime() - 3600 * 1000 * 24 * 7);
              picker.$emit("pick", date);
            },
          },
        ],
      },
    };
  },
  methods: {
    async submitForm() {
      this.$refs.kform.validate((valid, errInfo) => {
        if (valid) {
          this.$notify({
            title: "成功",
            message: JSON.stringify(this.formData),
            type: "success",
          });
        } else {
          try {
            Object.keys(errInfo).forEach((item) => {
              this.$message.error(errInfo[item][0].message);
              throw Error(errInfo[item][0].message);
            });
            // eslint-disable-next-line no-empty
          } catch (_) {}
        }
      });
    },
    //重置
    resetForm() {
      this.$refs.kform.resetFields();
    },
  },
};
</script>

<style>
.el-notification {
  word-wrap: break-word;
  word-break: break-all;
}
body,html{
padding: 0px;
  margin: 0px;
}
#app {
    padding: 10px;
  }
</style>
