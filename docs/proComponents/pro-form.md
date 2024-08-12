---
---
# pro-form
基于 `pms-form-row`、`el-form`的表单组件  
> el-form-item支持的类型有：`text` `textarea` `number` `select` `pmsSelect` `dates` `radio` `check` `inputTree` `inputMore` `switch`

## 基础用法
利用了 `pms-form-row` 组件自适应能力，只需配置对象数组*columns*，即可实现自适应布局
```vue
<template>
  <pro-form 
    ref="form"
    :columns="columns"
  />
</template>
<script>
export default {
  data() {
    return {
      columns: [
        {
          prop: 'contractName',
          label: '合同名称',
          type: 'text',
          isRequire: true, //是否必填
          className: 'wholeLine', //'wholeLine': 独占一行 'halfLine': 占半行
          breakRow: true, //下一个成员是否换行
        },{
          prop: 'orgName',
          realProp: 'orgId' //type为inputTree、inputMore时，选中数据额外参数下标 
          label: '单位',
          type: 'inputTree',
          loadApi: () => {}, //inputTree 且使用懒加载时 点击展开请求函数
        }
      ]
    }
  }
}
</script>
```
## API
::: tip
例如：el-form pms-form-row 列描述对象中的属性，***pro-form均支持***，***包括 attrs、listeners***在此不再赘述，请移步至对应API文档查看。  
:::
| 参数 | 说明 | 参数类型 | 默认值 |
| ------- | ---- | ------ | ----- |
| formConfig | 表单配置描述  | `object` | 参考el-form pms-form-row |
| columns    | 表单列的配置描述，具体项见下表  | `array` | - |
| dicts      | 表单字典  | `object` | - |
| dictName   | 字典别名  | `object` | - |
| formValue  | 默认表单数据  | `object` | - |

### formConfig
pro-form 表单表述对象，支持`el-form` `pms-form-row`的属性  
***组件自定义的属性***
| 参数 | 说明 | 参数类型 | 默认值 |
| ------- | ---- | ------ | ----- |  
| onlyView | 是否只读  | `boolean` | false |
| changeMoreSelect | 下拉框字典数据超出此值，切换成弹窗选择  | `number` | - |

### column
列描述数据对象，是columns中一项，column使用相同的API  

***组件自定义的属性***
| 参数 | 说明 | 参数类型 | 默认值 |
| ------- | ---- | ------ | ----- |
| type       | 对应上面介绍的`11`种表单成员类型  | `string` | - |
| isRequire  | 是否必填  | `boolean` | - |
| className  | `'wholeLine'`: 独占一行 `'halfLine'`: 占半行  | `string` | - |
| wholeLine  | 是否独占一行  | `boolean` | 无 |
| breakRow   | 下一个成员是否换行  | `boolean` | 无 |
| loadApi   | type为 inputTree 且使用懒加载时 点击展开请求函数  | `function` | 无 |
| realProp   | type为inputTree、inputMore时，选中数据额外参数下标  | `string` | 无 |

### dicts
pro-form 表单表述对象，支持`el-form` `pms-form-row`的属性  
***组件自定义的属性***
| 参数 | 说明 | 参数类型 | 默认值 |
| ------- | ---- | ------ | ----- |  
| onlyView | 是否只读  | `boolean` | false |
| changeMoreSelect | 下拉框字典数据超出此值，切换成弹窗选择  | `number` | - |



