<template>
  <div id="app">
    <Carousel />
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
      <KFormItem label="活动区域">
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

      <KFormItem label="特殊资源">
        <KRadioGroup v-model="formData.Special">
          <KRadio label="1">线上品牌商赞助</KRadio>
          <KRadio label="2">线下场地免费</KRadio>
        </KRadioGroup>
      </KFormItem>

      <KFormItem label="活动性质">
        <KCheckboxGroup v-model="formData.Nature">
          <KCheckbox label="美食/餐厅线上活动" name="type"></KCheckbox>
          <KCheckbox label="地推活动" name="type"></KCheckbox>
        </KCheckboxGroup>
      </KFormItem>

      <KFormItem label="阅读指南">
        <KCascader style="width:100%" :options="options" v-model="formData.Cascader" />
      </KFormItem>

      <el-button type="primary" @click="submitForm('kform')">提交</el-button>
      <el-button @click="resetForm('kform')">重置</el-button>
    </KForm>
  </div>
</template>

<script>
import Carousel from "./Carousel.vue";
import KForm from "./components/KForm.vue";
import KFormItem from "./components/KFormItem.vue";
import KInput from "./components/KInput.vue";
import KInputNumber from "./components/KInputNumber.vue";
import KSelect from "./components/KSelect.vue";
import KOption from "./components/KOption";
import KDatePicker from "./components/KDatePicker";
import KTimePicker from "./components/KTimePicker";
import KRate from "./components/KRate";
import KSlider from "./components/KSlider";
import KSwitch from "./components/KSwitch";
import KRadio from "./components/KRadio";
import KRadioGroup from "./components/KRadioGroup";
import KCheckbox from "./components/KCheckbox";
import KCheckboxGroup from "./components/KCheckboxGroup";
import KCascader from "./components/KCascader";
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
    KRadio,
    KSwitch,
    KRadioGroup,
    KCheckbox,
    KCheckboxGroup,
    KCascader,
  },
  data() {
    return {
      formData: {
        UserName: "",
        PassWord: "",
        ActionDay: "",
        ActionTime: "",
        Region: "",
        Nature: [],
        Counter: 0,
      },
      options: [
        {
          value: "zhinan",
          label: "指南",
          children: [
            {
              value: "shejiyuanze",
              label: "设计原则",
              children: [
                {
                  value: "yizhi",
                  label: "一致",
                },
                {
                  value: "fankui",
                  label: "反馈",
                },
                {
                  value: "xiaolv",
                  label: "效率",
                },
                {
                  value: "kekong",
                  label: "可控",
                },
              ],
            },
            {
              value: "daohang",
              label: "导航",
              children: [
                {
                  value: "cexiangdaohang",
                  label: "侧向导航",
                },
                {
                  value: "dingbudaohang",
                  label: "顶部导航",
                },
              ],
            },
          ],
        },
        {
          value: "zujian",
          label: "组件",
          children: [
            {
              value: "basic",
              label: "Basic",
              children: [
                {
                  value: "layout",
                  label: "Layout 布局",
                },
                {
                  value: "color",
                  label: "Color 色彩",
                },
                {
                  value: "typography",
                  label: "Typography 字体",
                },
                {
                  value: "icon",
                  label: "Icon 图标",
                },
                {
                  value: "button",
                  label: "Button 按钮",
                },
              ],
            },
            {
              value: "form",
              label: "Form",
              children: [
                {
                  value: "radio",
                  label: "Radio 单选框",
                },
                {
                  value: "checkbox",
                  label: "Checkbox 多选框",
                },
                {
                  value: "input",
                  label: "Input 输入框",
                },
                {
                  value: "input-number",
                  label: "InputNumber 计数器",
                },
                {
                  value: "select",
                  label: "Select 选择器",
                },
                {
                  value: "cascader",
                  label: "Cascader 级联选择器",
                },
                {
                  value: "switch",
                  label: "Switch 开关",
                },
                {
                  value: "slider",
                  label: "Slider 滑块",
                },
                {
                  value: "time-picker",
                  label: "TimePicker 时间选择器",
                },
                {
                  value: "date-picker",
                  label: "DatePicker 日期选择器",
                },
                {
                  value: "datetime-picker",
                  label: "DateTimePicker 日期时间选择器",
                },
                {
                  value: "upload",
                  label: "Upload 上传",
                },
                {
                  value: "rate",
                  label: "Rate 评分",
                },
                {
                  value: "form",
                  label: "Form 表单",
                },
              ],
            },
            {
              value: "data",
              label: "Data",
              children: [
                {
                  value: "table",
                  label: "Table 表格",
                },
                {
                  value: "tag",
                  label: "Tag 标签",
                },
                {
                  value: "progress",
                  label: "Progress 进度条",
                },
                {
                  value: "tree",
                  label: "Tree 树形控件",
                },
                {
                  value: "pagination",
                  label: "Pagination 分页",
                },
                {
                  value: "badge",
                  label: "Badge 标记",
                },
              ],
            },
            {
              value: "notice",
              label: "Notice",
              children: [
                {
                  value: "alert",
                  label: "Alert 警告",
                },
                {
                  value: "loading",
                  label: "Loading 加载",
                },
                {
                  value: "message",
                  label: "Message 消息提示",
                },
                {
                  value: "message-box",
                  label: "MessageBox 弹框",
                },
                {
                  value: "notification",
                  label: "Notification 通知",
                },
              ],
            },
            {
              value: "navigation",
              label: "Navigation",
              children: [
                {
                  value: "menu",
                  label: "NavMenu 导航菜单",
                },
                {
                  value: "tabs",
                  label: "Tabs 标签页",
                },
                {
                  value: "breadcrumb",
                  label: "Breadcrumb 面包屑",
                },
                {
                  value: "dropdown",
                  label: "Dropdown 下拉菜单",
                },
                {
                  value: "steps",
                  label: "Steps 步骤条",
                },
              ],
            },
            {
              value: "others",
              label: "Others",
              children: [
                {
                  value: "dialog",
                  label: "Dialog 对话框",
                },
                {
                  value: "tooltip",
                  label: "Tooltip 文字提示",
                },
                {
                  value: "popover",
                  label: "Popover 弹出框",
                },
                {
                  value: "card",
                  label: "Card 卡片",
                },
                {
                  value: "carousel",
                  label: "Carousel 走马灯",
                },
                {
                  value: "collapse",
                  label: "Collapse 折叠面板",
                },
              ],
            },
          ],
        },
        {
          value: "ziyuan",
          label: "资源",
          children: [
            {
              value: "axure",
              label: "Axure Components",
            },
            {
              value: "sketch",
              label: "Sketch Templates",
            },
            {
              value: "jiaohu",
              label: "组件交互文档",
            },
          ],
        },
      ],
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
body,
html {
  padding: 0px;
  margin: 0px;
}
#app {
  padding: 10px;
}
</style>
