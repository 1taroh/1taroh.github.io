# 1taroh.github.io

```math
\frac{d^2}{dt^2} \boldsymbol{v} = \nabla^2 \boldsymbol{v}
```

## 備忘録

github pages 用にローカルマシンでbundle install しようとしたらエラーが出たので対処法をメモします。

###　問題発生までの流れ
[getting started](https://docs.github.com/ja/pages/setting-up-a-github-pages-site-with-jekyll/creating-a-github-pages-site-with-jekyll) に従って
`gem "jekyll"`で始まる行をコメントアウトし、`# gem "github-pages"`で始まる行を以下のように編集しました。
```gemfile
gem "github-pages", "~> GITHUB-PAGES-VERSION", group: :jekyll_plugins
```
ここで`bundle install`すれば良いらしいのですが、以下のようにエラーが発生。

```bash
<USERNAME>.github.io/docs$ bundle install

[!] There was an error parsing `Gemfile`: Illformed requirement ["~> GITHUB-PAGES-VERSION"]. Bundler cannot continue.

 #  from <USERNAME>.github.io/docs/Gemfile:15
 #  -------------------------------------------
 #  # uncomment the line below. To upgrade, run `bundle update github-pages`.
 >  gem "github-pages", "~> GITHUB-PAGES-VERSION", group: :jekyll_plugins
 #  # If you have any plugins, put them here!
 #  -------------------------------------------
```

## 試したこと
githb-pages のテーマがローカルで必要なのかと思い、
```
gem install github-pages
```
を実行した。
これでも`bundle install`できなかったので、
```
gem "github-pages", "~> GITHUB-PAGES-VERSION", group: :jekyll_plugins
```
を以下のように書き換えた。
```
gem "github-pages"
```
これで`bundle install`すると通ったのでヨシ！
これだとバージョン云々でリスクがあるが、動かないよりまし。

## 参考文献
* [wsl2にrubyをインストールして、Jekyllを使えるようにするまで](https://qiita.com/orengepy/items/b6de3ae7655ee53cf381)