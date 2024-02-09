<template>
  <div class="card content-box">
    <el-alert
      title="通过 component :is 组件属性 && v-bind 属性透传，可以将 template 中的 html 代码全部改变为 columns 配置项，具体配置请看代码。"
      type="warning"
      :closable="false"
    />
    <component :is="'el-form'" v-bind="options.form" ref="proFormRef" :model="model">
      <template v-for="item in options.columns" :key="item.prop">
        <component :is="'el-form-item'" v-bind="item.formItem">
          <component :is="`el-${item.attrs.typeName}`" v-bind="item.attrs" v-model="model[item.formItem.prop]" />
        </component>
      </template>
      <el-form-item>
        <slot name="operation"></slot>
      </el-form-item>
    </component>
  </div>
</template>

<script setup lang="ts" name="proForm">
import { ref } from "vue";

let model = ref<any>({});

const options = ref({
  // 表单整体配置项
  form: {
    inline: false,
    labelPosition: "right",
    labelWidth: "80px",
    size: "default",
    disabled: false,
    labelSuffix: " :"
  },
  // 表单列配置项 (formItem 代表 item 配置项，attrs 代表 输入、选择框 配置项)
  columns: [
    {
      formItem: {
        label: "设计煤收到基碳",
        prop: "tan",
        labelWidth: "200px",
        required: true
      },
      attrs: {
        typeName: "input",
        clearable: true,
        placeholder: "请输入",
        style: "width:500px"
        // disabled: true
      }
    },
    {
      formItem: {
        label: "设计煤收到基氢",
        prop: "qing",
        labelWidth: "200px",
        required: true
      },
      attrs: {
        typeName: "input",
        placeholder: "请输入",
        clearable: true,
        style: "width:500px"
      }
    },
    {
      formItem: {
        label: "设计煤收到基氧",
        prop: "yang",
        labelWidth: "200px",
        required: true
      },
      attrs: {
        typeName: "input",
        placeholder: "请输入",
        clearable: true,
        style: "width:500px"
      }
    },
    {
      formItem: {
        label: "设计煤收到基氮",
        prop: "dan",
        labelWidth: "200px",
        required: true
      },
      attrs: {
        typeName: "input",
        clearable: true,
        placeholder: "请输入",
        style: "width:500px"
        // disabled: true
      }
    },
    {
      formItem: {
        label: "设计煤收到基硫",
        prop: "liu",
        labelWidth: "200px",
        required: true
      },
      attrs: {
        typeName: "input",
        clearable: true,
        placeholder: "请输入",
        style: "width:500px"
        // disabled: true
      }
    },
    {
      formItem: {
        label: "设计煤收到基灰分",
        prop: "huifen",
        labelWidth: "200px",
        required: true
      },
      attrs: {
        typeName: "input",
        clearable: true,
        placeholder: "请输入",
        style: "width:500px"
        // disabled: true
      }
    },
    {
      formItem: {
        label: "全水分",
        prop: "shuifen",
        labelWidth: "200px",
        required: true
      },
      attrs: {
        typeName: "input",
        clearable: true,
        placeholder: "请输入",
        style: "width:500px"
        // disabled: true
      }
    },
    {
      formItem: {
        label: "设计煤收到基低位发热量",
        prop: "liu",
        labelWidth: "200px",
        required: true
      },
      attrs: {
        typeName: "input",
        clearable: true,
        placeholder: "请输入",
        style: "width:500px"
        // disabled: true
      }
    }
  ]
});
</script>

<style scoped lang="scss">
@import "./index.scss";
</style>
