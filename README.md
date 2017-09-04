# 复选框组件

## 基于vue视觉组件

主要配合[pcadmin](https://github.com/ksc-fx/pcadmin)使用。
使用方法：
```
npm install pcadmin-checkbox
```

```javascript

import checkbox from 'pcadmin-checkbox';

```

### Data
| 参数      | 说明          | 类型      | 是否必选                           | 可选值  | 默认值  |
|---------- |-------------- |---------- |--------------------------------  |-------- |-------- |
| checked | 是否勾选 | Boolean | - | true:勾选，false:不勾选 | false |


### Events
| 事件名称 | 说明 | 回调参数 |
|---------- |-------- |---------- |
| change | 当勾选值变化时触发 | event 事件对象 |