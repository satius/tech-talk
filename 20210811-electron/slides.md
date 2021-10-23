---
marp: true
theme: gaia
header: "Electron を触ってDesktopアプリについて考えた"
footer: "by Sugiyama"
paginate: true
---

<!--
_class: lead
_paginate: false
_header: ""
_footer: ""
-->

# Electron を触って

# Desktop アプリについて考えた

### 2021/08/11 Sugiyama

---

![height:50](https://camo.githubusercontent.com/2ef2a441f9eaa1aca489796981cfa851d9388e08209b08e57526a06b4e604a57/68747470733a2f2f656c656374726f6e6a732e6f72672f696d616765732f656c656374726f6e2d6c6f676f2e737667)

# Electron とは? (1)

- デスクトップアプリケーション開発フレームワーク
- クロスプラットフォーム
  - Windows
  - macOS
  - Linux
- 開発元は Github
  - github.com/electron/electron

---

![height:40](https://camo.githubusercontent.com/2ef2a441f9eaa1aca489796981cfa851d9388e08209b08e57526a06b4e604a57/68747470733a2f2f656c656374726f6e6a732e6f72672f696d616765732f656c656374726f6e2d6c6f676f2e737667)

# Electron とは? (2)

- 公式事例集: electronjs.org/apps
  - Atom![height:24](https://www.electronjs.org/images/app-img/atom/atom-icon-128.6ffc1bc8d483d555cc61b9866b581501.png#center)
    - もともと Electron は Atom を開発するためのフレームワーク
  - Visual Studio Code![height:24](https://www.electronjs.org/images/app-img/visual-studio-code/visual-studio-code-icon-128.3ca7557574f5ebd496c820340410fe7a.png)
  - Slack![height:24](https://www.electronjs.org/images/app-img/slack/slack-icon-128.fc16045e383d32da3526bf715b0bb27c.png)
  - Skype![height:24](https://www.electronjs.org/images/app-img/skype/skype-icon-128.5c86ab85293de6e7e1a14e85eda08929.png)
  - GitKraken![height:24](https://www.electronjs.org/images/app-img/gitkraken/gitkraken-icon-128.5654263dc2e210ce1f8c6fdb01ebbc9d.png)

---

![height:50](https://camo.githubusercontent.com/2ef2a441f9eaa1aca489796981cfa851d9388e08209b08e57526a06b4e604a57/68747470733a2f2f656c656374726f6e6a732e6f72672f696d616765732f656c656374726f6e2d6c6f676f2e737667)

# Electron とは? (3)

- 公式には載ってないけど Electron 使用
  - Authy![height:24](https://cdn-ssl-devio-img.classmethod.jp/wp-content/uploads/2014/12/authy.png)
  - Trello![height:24](https://is5-ssl.mzstatic.com/image/thumb/Purple125/v4/18/46/31/18463109-c612-c054-c540-19bb7aea84e7/AppIcon-0-1x_U007emarketing-0-7-0-0-85-220.png/230x0w.webp)
  - WorkFlowy![height:24](https://is1-ssl.mzstatic.com/image/thumb/Purple125/v4/e7/d9/81/e7d98173-084f-6bbe-bf78-56cfc1082dd1/AppIcon-0-0-1x_U007emarketing-0-0-0-10-0-0-sRGB-0-0-0-GLES2_U002c0-512MB-85-220-0-0.png/230x0w.webp)
  - Docker GUI![height:24](https://www.docker.com/sites/default/files/d8/styles/role_icon/public/2019-07/Moby-logo.png?itok=sYH_JEaJ)

---

# なぜデスクトップアプリなのか？(1)

##### (= なにが Web アプリでは難しいのか？)

- 動くものがホスト PC にあるので起動・動作が早い
  - ユーザーが、目当てのものにすぐアクセスできる
    - Authy
- ホストに対してできることが多い
  - ローカルのファイルシステムへの読み書き
    - Visual Studio Code 　(ディレクトリ単位での管理)
  - コマンドの実行
    - GitKraken (git init, git clone, etc...)

---

# なぜデスクトップアプリなのか？(2)

##### (= なにが Web アプリでは難しいのか？)

- バックグラウンドでプロセスが持てる
  - Slack(開いてなくても通知が受け取れる)

---

# Web アプリの方が強い点

- インストール不要
- アップデートが早い(ユーザーにアップグレードを促す必要がない)

---

<!-- _class: lead -->

### PWA...(あまり言及しない)

---

<!-- _class: lead -->

# ここで Electron の話に戻って...

---

![bg right 84%](./img/electron_image.jpg)

# Electron の中身

- Node.js
  - メインプロセス (サーバサイド js 相当)
    - ホストを操作できる
    - ウィンドウを管理する
  - レンダラプロセス (Web フロント相当)
    - Chromium
    - 複数存在しうる

---

# 何を作ればデスクトップアプリとしての価値を出せるのか？

##### (最大の課題)

- Web アプリにはちょっと実現できない機能を実装する
  - ホストのストレージ上のファイルを管理する
  - コマンドラインをラップする
  - Tray(常に目に付く場所)で何かを常に(有意義なことを)表示する
  - ホスト側でしかできない煩雑な操作を代行する

---

<!-- _class: lead -->

### "何か"をつくった

---

## <!-- ### (何かって何を？......) -->

## `SBM`: macセットアップ支援アプリ の空想(1)

- カスタマイズの面倒な調整を解消する
  - いわゆる`Preferences`
    - Dock の位置/Autohide
    - ダークモード/ライトモード
    - マウスカーソルの速さ
    - 外部ディスプレイとの位置関係
  - ~/.zshrc の内容
  - Homebrew の利用状況

---

## `SBM`: macセットアップ支援アプリ の空想(2)

- 想定
  - 普段の PC に予め SBM をインストールしておく
  - 新しい PC を手に入れたら早めに SBM をインストールする
- 何をするのか
  - macOS の設定変更を監視
  - macOS の設定内容を YAML などの設定ファイルに常にエクスポート
  - 設定ファイルはローカルの git リポジトリで管理
  - 設定ファイルをインポートし即座に新しい macOS に適用する

---

# やりたかったけどできなかった

- レンダラプロセスで Vue.js/React を用いて描画
- 開発環境
  - 仮想化
  - ホットリロード
- 各種テスト

---

# 感想

- Electron でいろいろできそうではある
- 意義のあることを発想するのは難しい
- 自分 Node.js 全然知らないなと思った
  - TypeScript に移行するのが意外としんどかった

---

<!--
_class: lead
_paginate: false
_header: ""
_footer: ""
-->

# おわり

---

# 次はこれをやりたい

- 続・SBM をつくる
- 個人主義な TODO アプリをつくる
- 麻雀点箱アプリをつくる
- リモートクリップボードアプリをつくる
- Ethereum でなにかする
- ICP(Internet Computer Protocol)でなにかする
- (Marp でもう少し`らしい`スライドを作ってみる)

---

<!--
_class: lead
_paginate: false
_header: ""
_footer: ""
-->

# 本当におわり
