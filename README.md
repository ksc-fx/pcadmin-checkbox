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
| type | 按钮类型 | String | - | default:实心按钮白字，primary:白底按钮字体带颜色，text:字体按钮 | default |
| color | 按钮颜色 | String | - | green:绿色,red:红色,orange:橙色,blue:蓝色 | green |
| disabled | 是否有效可点击 | Boolean | — | true/false | true |
| params | 点击返回的参数，给什么返回什么。没有就返回event事件 | - | — |  - | — |


### Events
| 事件名称 | 说明 | 回调参数 |
|---------- |-------- |---------- |
| buttonClick | 点击回调函数 | — |