---
layout: post
title:  「以前のバージョン」の Microsoft IME で US 配列で日英切り替え
date:   2024-01-27 00:10:00 +0900
categories: Windows11
---

Microsoft IME のバージョンによっては，ネット上に転がっている情報と合致していないみたいで，新たに方法を開拓した．

## 環境
* windows 11 23H2
* 以前のバージョンのMircrosoft IME

## 方法
設定 > 時刻と言語 > 言語と地域 と進める．

![Alt text]({{site.baseurl}}/assets/images/image.png)

上図を参考に，
日本語 > 言語のオプション > Microsoft IME と進める．

![Alt text]({{site.baseurl}}/assets/images/image-1.png)

上図のように，
キーボードオプション > 全般 > 詳細設定(下の方にある) > 詳細設定を開く

編集操作の「キー設定」で「変更」をクリックする．

![Alt text]({{site.baseurl}}/assets/images/image-2.png){:width="400"}

画像で青塗りになっている部分を選択し，「変更」をクリックする．

![Alt text]({{site.baseurl}}/assets/images/image-3.png){:width="400"}

「IME-オン/オフ」を選択し，「OK」をクリックする．

下図のようになっていれば良い．

![Alt text]({{site.baseurl}}/assets/images/image-4.png){:width="400"}

「適用」を押せば ctrl+space で日英切り替えできるようになる．

正直，こんなことせず最新版の Microsoft IME を使えばよい気がする...