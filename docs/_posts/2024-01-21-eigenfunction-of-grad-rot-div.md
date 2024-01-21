---
layout: post
title:  ベクトル解析でよくみる微分作用素の固有関数
date:   2024-01-21 04:02:00 +0900
categories: eigenfunction
---
<script type="text/x-mathjax-config">MathJax.Hub.Config({tex2jax:{inlineMath:[['\$','\$'],['\\(','\\)']],processEscapes:true},CommonHTML: {matchFontHeight:false}});</script>
<script type="text/javascript" async src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.1/MathJax.js?config=TeX-MML-AM_CHTML"></script>

ある日，ふと思った...

「grad とか rot とか div とかって線形作用素やんか．固有関数ってなんなんや？」

google 検索ﾎﾟﾁｰ

なにもでてこない！！

ということで私が書きます．

## 微分作用素の線形性の確認
固有関数を求める前に，各微分作用素の線形性を確認しておきます．

$$
\begin{align}
    \mathrm{grad} \,f(\boldsymbol{x}) &= \sum_{i=1}^3\boldsymbol{e}_i\frac{\partial}{\partial x_i}f(\boldsymbol{x}) 
\end{align}
$$

であるので，

$$
\begin{align}
    \mathrm{grad} \,(af(\boldsymbol{x})+bg(\boldsymbol{x})) &= \sum_{i=1}^3\boldsymbol{e}_i\frac{\partial}{\partial x_i}(af(\boldsymbol{x})+bg(\boldsymbol{x})) \\
    &= a\sum_{i=1}^3\boldsymbol{e}_i\frac{\partial}{\partial x_i}f(\boldsymbol{x})
    + b\sum_{i=1}^3\boldsymbol{e}_i\frac{\partial}{\partial x_i}g(\boldsymbol{x}) \\
    &= a\,\mathrm{grad}\,f(\boldsymbol{x}) + b\,\mathrm{grad}\,g(\boldsymbol{x}).
\end{align}
$$

以上から， \\( \mathrm{grad} \\) は線形です．
つづいて\\( \mathrm{rot} \\)は，

$$
\begin{align}
    \mathrm{rot} \, \boldsymbol{v} &= 
      \left( \frac{\partial v_3}{\partial x_2} - \frac{\partial v_2}{\partial x_3} \right)\boldsymbol{e}_1
    + \left( \frac{\partial v_1}{\partial x_3} - \frac{\partial v_3}{\partial x_1} \right)\boldsymbol{e}_2
    + \left( \frac{\partial v_2}{\partial x_1} - \frac{\partial v_1}{\partial x_2} \right)\boldsymbol{e}_3
\end{align}
$$

であるので，

$$
\begin{align}
    \mathrm{rot} \, (a\boldsymbol{v}+b\boldsymbol{u}) &= 
      \left( \frac{\partial}{\partial x_2}(av_3+bu_3) - \frac{\partial}{\partial x_3}(av_3+bu_3) \right)\boldsymbol{e}_1
    + \left( \frac{\partial}{\partial x_3}(av_1+bu_1) - \frac{\partial}{\partial x_1}(av_1+bu_1) \right)\boldsymbol{e}_2
    + \left( \frac{\partial}{\partial x_1}(av_2+bu_2) - \frac{\partial}{\partial x_2}(av_2+bu_2) \right)\boldsymbol{e}_3
    \\
    &=
    a\left\{
      \left( \frac{\partial v_3}{\partial x_2} - \frac{\partial v_2}{\partial x_3} \right)\boldsymbol{e}_1
    + \left( \frac{\partial v_1}{\partial x_3} - \frac{\partial v_3}{\partial x_1} \right)\boldsymbol{e}_2
    + \left( \frac{\partial v_2}{\partial x_1} - \frac{\partial v_1}{\partial x_2} \right)\boldsymbol{e}_3
    \right\}
    \\
    & \quad +
    b\left\{
      \left( \frac{\partial v_3}{\partial x_2} - \frac{\partial v_2}{\partial x_3} \right)\boldsymbol{e}_1
    + \left( \frac{\partial v_1}{\partial x_3} - \frac{\partial v_3}{\partial x_1} \right)\boldsymbol{e}_2
    + \left( \frac{\partial v_2}{\partial x_1} - \frac{\partial v_1}{\partial x_2} \right)\boldsymbol{e}_3
    \right\} \\
    &=
    a\ \mathrm{rot}\,\boldsymbol{v} + b\ \mathrm{rot}\,\boldsymbol{u}
\end{align}
$$

以上から， \\( \mathrm{rot} \\) の線形性も示せました．最後に \\( \mathrm{div} \\) です．

$$
\begin{align}
    \mathrm{div} \ f(\boldsymbol{x}) &= \sum_{i=1}^3\frac{\partial}{\partial x_i}f(\boldsymbol{x}) 
\end{align}
$$

であるので，

$$
\begin{align}
    \mathrm{div} \ (af(\boldsymbol{x})+bg(\boldsymbol{x})) &= \sum_{i=1}^3\frac{\partial}{\partial x_i}(af(\boldsymbol{x})+bg(\boldsymbol{x})) \\
    &= a \sum_{i=1}^3\frac{\partial}{\partial x_i}f(\boldsymbol{x}) + b \sum_{i=1}^3\frac{\partial}{\partial x_i}g(\boldsymbol{x}) \\
    &= a\ \mathrm{div} \ f(\boldsymbol{x}) + b\ \mathrm{div} \ g(\boldsymbol{x}).
\end{align}
$$

以上により，\\(\ \mathrm{grad},\ \mathrm{rot},\ \mathrm{div} \\) はすべて線形作用素であることがわかりました．

## 固有関数の定義
線形作用素 \\( L \\) に対し，次式を満たす \\( x \\)が固有関数です．

$$
\begin{align}
    L[x] = \lambda x
\end{align}
$$

行列の固有値問題では \\( \lambda \\) はスカラーですが，ここでは固有関数の議論をしているので \\( \lambda \\) がスカラーかどうかを問わないことにします．
## 各作用素の固有関数
\\( \mathrm{grad} \\) を \\( \mathrm{e}^{\lambda_x x + \lambda_y y + \lambda_z z} \\) に作用させてみます．

$$
\begin{align}
    \mathrm{grad} \ \mathrm{e}^{\lambda_x x + \lambda_y y + \lambda_z z} &= 
    \begin{bmatrix}
        \lambda_x \\ \lambda_y \\ \lambda_z
    \end{bmatrix}
    \mathrm{e}^{\lambda_x x + \lambda_y y + \lambda_z z}
\end{align}
$$

どうでしょう... 固有関数としてありといえばありな気もします．

\\( \mathrm{rot} \\) を \\( [1 \ 1 \ 1]^\top (\mathrm{e}^{\lambda_x x}+\mathrm{e}^{\lambda_y y}+\mathrm{e}^{\lambda_z z}) \\) に作用させてみます．

$$
\begin{align}
    \mathrm{rot} \ 
    \begin{bmatrix}
        \mathrm{e}^{\lambda_x x} \\ \mathrm{e}^{\lambda_y y} \\ \mathrm{e}^{\lambda_z z}
    \end{bmatrix}
    &= 
    \begin{bmatrix}
        \lambda_z - \lambda_y & & \\ 
        & \lambda_x - \lambda_z & \\
        & & \lambda_y - \lambda_x
    \end{bmatrix}
    \begin{bmatrix}
        \mathrm{e}^{\lambda_x x} \\ \mathrm{e}^{\lambda_y y} \\ \mathrm{e}^{\lambda_z z}
    \end{bmatrix}
\end{align}
$$

なるほど．まあよしとしましょう．

最後に\\( \mathrm{div} \\) も \\( \mathrm{e}^{\lambda_x x + \lambda_y y + \lambda_z z} \\) に作用させてみます．

$$
\begin{align}
    \mathrm{div} \ \mathrm{e}^{\lambda_x x + \lambda_y y + \lambda_z z} &= 
    (\lambda_x + \lambda_y + \lambda_z) \mathrm{e}^{\lambda_x x + \lambda_y y + \lambda_z z}
\end{align}
$$

これは完全に固有関数です！

以上で各微分作用素の固有関数を求めてみる試みは終わりです．
線形作用素が行列の場合には，固有ベクトルの有限和で展開することができましたが，多くの場合，関数を固有関数で展開するのは無限和を使う必要があります．
しかし，固有関数で展開できると仮定してみるのは悪手とは言えません．みなさんご存知のフーリエ変換がそれに該当します．