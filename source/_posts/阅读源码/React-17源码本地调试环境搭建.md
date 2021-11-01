---
title: React 17源码本地调试环境搭建
date: 2021-09-30 13:01:55
tags: 源码
categories: 阅读源码
---
<style type="text/css">
.mt10 {
  margin-top: 10px;
}
.m10 {
  margin: 10px 0;
}
.pt10 {
  padding-top: 10px;
}
.red {
  color: red;
}
</style>

<p>为了更连贯了解React底层源码运行机制及原理，通过搭建源码层调试环境反复调试，加深对底层运行原理深入理解及作者对框架本身架构层的设计深化。</p>

<!-- more -->

<p>参考react源码调试环境搭建：https://zhuanlan.zhihu.com/p/336933386</p>

<p class="red">搭建过程中遇到的问题处理：</p>
<ol>
  <li>修改webpack配置
    <p class="m10">修改config/webpack.config.js</p>
    ```
    resolve: {
      alias: {
        'react-native': 'react-native-web',

        'react': path.resolve(__dirname, '../src/react/packages/react'),
        'react-dom': path.resolve(__dirname, '../src/react/packages/react-dom'),
        'shared': path.resolve(__dirname, '../src/react/packages/shared'),
        'react-reconciler': path.resolve(__dirname, '../src/react/packages/react-reconciler'),

        // 补充
        'react-devtools-scheduling-profiler': path.resolve(__dirname, '../src/react/packages/react-devtools-scheduling-profiler'),
        'react-devtools-shared': path.resolve(__dirname, '../src/react/packages/react-devtools-shared'),

        ...(isEnvProductionProfile && {
          'react-dom$': 'react-dom/profiling',
          'scheduler/tracing': 'scheduler/tracing-profiling',
        }),
        ...(modules.webpackAliases || {}),
      }
    }
    ```
  </li>

  <li>修改package.json的babel配置
    ```
    "babel": {
      "presets": [
        [
          "react-app",
          {
            "runtime": "automatic"
          }
        ]
      ]
    }
    ```
  </li>
</ol>

<h4 style="margin-top:50px;"><附></h4>
参考：
<ol>
  <li>react源码调试环境搭建：https://zhuanlan.zhihu.com/p/336933386</li>
  <li>ReferenceError: React is not defined 报错解决方法：https://blog.csdn.net/qq_38605121/article/details/109390989</li>
</ol>
