---
title: "WorkLog"
date: 2019-08-17T12:09:50+09:00
draft: true
toc: false
images:
tags:
  - Chrome拡張
  - TypeScript
  - Gulp
  - Yeoman
---

業務でタスクにかかった時間をまとめて提出するのですが、テキストファイルで管理するのは面倒。
あとで集計するのも面倒。
なのである程度自動化しようと思い、ツールを開発することにしました。

デスクトップアプリなどは時間がかかり面倒なので、Chrome の拡張機能としてパパっと開発することにしました。


## 開発環境の構築

---

基本的にコチラを参考にしました。
https://qiita.com/Takumon/items/da2142cc06b243f83211

####  1. 必要ソフトのインストール

```
$ npm i -g yo generator-chrome-extension-kickstart-typescript
```

- yo
  - Yeoman は Web アプリの雛形を自動生成するためのツール
  - generator というテンプレートがありこれで簡単に雛形が作成できる
- generator-chrome-extension-kickstart-typescript
  - Chrome の拡張を TypeScript で開発するための Yeoman の generator

#### 2. 雛形の作成

```
$ mkdir my-app
$ cd my-app
$ yo chrome-extension-kickstart-typescript
```

#### 3. 質問に答える

- What would you like to call this extension?  
  -> プロジェクト名の入力（デフォルトはフォルダ名）
- And how would you call it if you only had 12 characters (short_name)?  
  -> 12文字以内で短い略称を入力（デフォルトはフォルダ名）
- How would you like to describe this extension?  
  -> プロジェクトの説明を入力
- Would you like to use UI Action?  
  -> No ... UI Action を使用しない  
  -> Browser ... ツールバーにアイコンが常駐する  
  -> Page ... 特定の Web サイトのみでツールバーにアイコンが表示される  
- Would you like to override a chrome page?  
  -> Chrome 内部のページを書き換えるかどうかで、書き換えるページを選択
- Would you like more UI Features?  
  -> Options Page ... 設定画面を作る場合  
  -> Devtools Page ... デベロッパーツールを拡張する場合  
  -> COntent Scripts ... 表示している Web ページを拡張する場合  
  -> Omnibox ... アドレスバーを拡張したい場合  
- Would you like to use permissions?  
  -> Chrome 拡張で使用する API のパーミッションを選択  
- Would you like to install promo images for the Chrome Web Store?  
  -> Chrome ウェブストアのプロモーション用画像を自動生成するか

Chrome 拡張で設定できるパーミッションの一覧
https://developer.chrome.com/extensions/declare_permissions

## 出来上がった Chrome 拡張を動かしてみる

---

```
$ yarn dev:chrome
```

しかし gulp@3.9.1 を利用していると `Failed to load external module @babel/register` というエラーが出るので
3.9.0 を明示的にインストールします。

```
$ yarn add -D gulp@3.9.0
```

これでエラーがなくなりました。
