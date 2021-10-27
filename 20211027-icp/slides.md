---
marp: true
theme: gaia
header: "ICP上にアプリケーションをデプロイするということ"
footer: "by Sugiyama"
paginate: true

---

<!--
_class: lead
_paginate: false
_header: ""
_footer: ""
-->

# ICP上にアプリケーションを
# デプロイするということ

### 2021/10/27 Sugiyama

---

<!--
_class: lead
_paginate: false
_header: ""
_footer: ""
-->
# <!-- fit --> * ブロックチェーンな話題を含みます

---

<!--
_class: lead
_paginate: false
_header: ""
_footer: ""
-->
# <!-- fit --> とりあえずFleekで適当なWebサイトをホスティング
app.fleek.co

---
![height:70](https://i1.wp.com/terminalco.wpcomstaging.com/wp-content/uploads/2020/03/FleekForLight.png)

### ...とはなんなのか

- Fleek makes it easy to build websites and apps on the new open web: permissionless, trustless, censorship resistant, and free of centralized gatekeepers.
- オープンウェブ思想
- <span style="color:blue;">ICP</span>上にアプリケーションをデプロイできる
- 無料プランでは ビルド時間250分/月
- よくあるSaaS風 Firebaseっぽい(個人の感想)

---

<!--
_class: lead
_paginate: false
_header: ""
_footer: ""
-->

# <span style="color:blue;">ICP</span>とは

---

<!--
_class: lead
_paginate: false
_header: ""
_footer: "(マジカヨ)"
-->

# <!-- fit --><span style="color:blue;">インターネット・コンピューター</span>

---

<!--
_class: lead
_paginate: false
_header: ""
_footer: ""
-->

# <!-- fit --><span style="color:blue;">インターネット・コンピューター</span>
# (・プロトコル)

---

![height:70](https://dfinity.org/static/logo-a810b89ac5628fbfe3f7f0b8e24f5c26.png)

### インターネット・コンピューター・プロトコル (ICP)
- Dfinity (非営利財団)
- パブリックブロックチェーン
- 世界中の独立したデータセンターを使って分散型クラウドを目指す(<span style="color:red;">AWSやGoogle Cloudをブロックチェーンで実現したい</span>)
- オープンソース https://github.com/dfinity/ic


---

![bg　contain](https://lh3.googleusercontent.com/QcomaqtOeAxAOmqTpQP89fb47Qd7QummHmF7TIpRgAMPIQ_Ga5vGGIOIxi9ohIWGKMu-0Eo5ewkZ2gvBW2h-biIhr4fd3Lal_qTitskb-8VR7x9jbNH_rU0ACTbb7iUOcgzJ-bLM)

---
### 分散型クラウドの利点

- 止まらない(障害がほぼ起こらない)
- コンテンツが制限されない
- データが失われない、改ざんされない

---

### キャニスター
ICP上の1単位。アプリケーションはキャニスターを1つ以上もつ。
キャニスターはWASMコードとメモリで構成される。
キャニスターはICPトークンによって計算リソースを得る。

![image　height:320](https://www.cxr-inc.com/pkobo_news/upload/37-3.png?61788eefbc88e)

---

### ICPトークンの利用
- サイクル(計算リソース)に替える
- 資産として交換する
- ガバナンスに対して投票する権利を得る
![image　height:320](https://www.cxr-inc.com/pkobo_news/upload/37-4.png?61788eefbc890)



---

### Ethereum vs ICP
- ETHはストレージを持てない
-> Webサイトのホストなどはできない
- ICPは1アプリケーションに割り当てられるノード数が少ない(7つほど)ので、ノード間の通信が早く、アプリとして速度を出せる

### EthereumとICPの共存
- WebフロントをICPでホストし、Ethereumのスマートコントラクトを呼び出す

---

### 疑問点
- ICPにデプロイしたアプリケーションが 分散していることをどうやって検証する？
- 独自ドメインの割り当てしても非中央集権？

---

<!--
_class: lead
_paginate: false
_header: ""
_footer: ""
-->

# おわり
誰かホワイトペーパー読んでください
