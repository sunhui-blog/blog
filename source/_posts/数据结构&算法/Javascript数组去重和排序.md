---
title: Javascript数组去重和排序
date: 2020-12-13 10:27:19
tags: 算法
categories: 数据结构&算法
---

<style type="text/css">
.red {
  color: red;
}
</style>

数组去重和排序

<!--more-->

<h4>数组去重: 包含null/undefined</h4>
<ol>
  <li>es6的Set
    ```
    function unique (arr) {
      return [...new Set(arr)]
    }

    function unique (arr) {
      return Array.from(new Set(arr));
    }

    unique(['a', 'a', 'b', 'c']) // ['a', 'b', 'c']
    ```
  </li>
  <li>indexOf()结合for...of/forEach/for...in
    ```
    const arr = [1, 1, 2, 3, 4, 4, 5, 6, 6];

    function unique (arr) {
      const newArr = [];
      for(let item of arr){
        if (newArr.indexOf(item) === -1) {
          newArr.push(item)
        }
      }

      return newArr
    }
    ```
  </li>
  <li>includes()结合for...of/forEach/for...in
    ```
    function unique (arr) {
      const newArr = [];
      for(let item of arr){
        if (!newArr.includes(item)) {
          newArr.push(item)
        }
      }

      return newArr
    }
    ```
  </li>
  <li>双重for循环，<span class="red">时间复杂度为O(n^2)</span>
    ```
    function unique (arr) {
      const newArr = []
      let isRepeat = false
      for (let item of arr) {
        isRepeat = false
        for (let newItem of newArr) {
          if (item === newItem) {
            isRepeat = true
          }
        }

        if (!isRepeat) {
          newArr.push(item)
        }
      }

      return newArr
    }
    ```

    优化版
    ```
    function unique (arr) {
      const newArr = []
      const len = arr.length
      for (let i = 0; i < len; i++) {
        for (let j = i + 1; j < len; j++) {
          if (arr[i] === arr[j]) {
            j = ++i
          }
        }
        newArr.push(arr[i])
      }

      return newArr
    }
    ```
  </li>
</ol>

<h4>数组排序</h4>
<ol>
  <li>sort()
    ```
    const arr=[1, 11, 2, 3, 6]
    arr.sort((a, b) => {
      return a - b
    })
    arr // output: [1, 2, 3, 6, 11]
    ```

    注：默认排序规则是数组元素字符的Unicode编码排序的，也就是说数组元素会被当做字符串，然后按照字符串的Unicode编码进行升序排列。
  </li>
</ol>
