---
title: "Vue Store の getter でクロージャーを使う方法"
date: 2019-11-16T19:48:57+09:00
tags:
  - vue
  - vuex
  - vue-compositoin-api
  - getters
  - closure
---

Vue で Store の getter を書いているときに引数によって戻り値を変えたいときがある。  
そんなときには以下の方法でデータを絞り込むことが可能だ。

## vuex

```ts
const getters = {
  getByID: (state) => (id: strig) => state.todos.find(t => t.id === id)
}
```

## vuex-compositoin-api

```ts
const state = reactive({ ... })
const getByID = computed(() => (id: string) => state.todos.find(t => t.id === id))
```

## 参考

- https://ema-hiro.hatenablog.com/entry/2019/01/08/033121
- https://qiita.com/ryo2132/items/f055679e9974dbc3f977
