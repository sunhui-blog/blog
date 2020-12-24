---
title: Vue问题总结
date: 2019-10-28 23:09:34
tags: 框架
categories: 框架
---

<p>常见问题总结</p>

<!-- more -->

<ol>
  <li>父组件给子组件传props，当props值不需设置时，可传null或者undefined
    ```
    props: {
      // 基础的类型检查 (`null` 和 `undefined` 会通过任何类型验证)
      propA: Number,
      // 多个可能的类型
      propB: [String, Number],
      // 必填的字符串
      propC: {
        type: String,
        required: true
      },
      // 带有默认值的数字
      propD: {
        type: Number,
        default: 100
      },
      // 带有默认值的对象
      propE: {
        type: Object,
        // 对象或数组默认值必须从一个工厂函数获取
        default: function () {
          return { message: 'hello' }
        }
      },
      // 自定义验证函数
      propF: {
        validator: function (value) {
          // 这个值必须匹配下列字符串中的一个
          return ['success', 'warning', 'danger'].indexOf(value) !== -1
        }
      }
    }
    ```
  </li>
  <li>在某个页面中new一个对象时，在离开页面时要注意销毁（设为undefined）,避免对象被实例化多次。</li>
</ol>
