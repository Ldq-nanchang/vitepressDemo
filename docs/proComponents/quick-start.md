---
title: 'abc'
outline: deep
---
# 快速上手
::: tip
当前使用方式是，作为子仓库拉取至libs文件夹下，非npm仓库安装
:::

## 关联子仓库
关联子仓库后，写入配置文件指令集中
使用 `npm run merge:libs` 命令更新子仓库代码

**packages.json**
```json{2}
"scripts" : {
  "merge:libs": "git pull http://gitlab.nrxt.com/pms30/jihua/vuecomon/pms-plan-nation-admin.git master --allow-urelated-histories"
}
```
## 引入
全局引用

**main.js**
```js
import LibsComponents form '@/libs/components'
Vue.use(LibsComponents)
```
### 组件库全局配置option

```js
const option = {
  layout: {
    "root-padding": "0"
  }
}
Vue.use(LibsComponents, option)
```
### option全局参数配置表 
| 参数名称 | 说明 | 参数类型 | 默认值 |
| ------- | ---- | ------ | ----- |
| form    | 表单  | object | 参考el-form |
| table    | 表格  | object | 参考el-table |
| pagination| 分页  | object | 参考el-pagination |
| layout    | 布局  | object | 无 |
| shadowForm | 表格内表单  | object | 无 |
| hooksStore    | 钩子函数  | object | 无 |

### beforeQueryData()
pro-table的props中queryData函数执行前执行
+ 示例
```js
hooksStore: {
  beforeQueryData: (param) => { // [!code focus]
    // param是搜索栏中+默认入参的混合对象，可对它自定义 // [!code focus]
    return param // [!code focus]
  } // [!code focus]
}

```
