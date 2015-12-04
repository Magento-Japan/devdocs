---
layout: default
group: arch-guide
subgroup: Architectural Basics
title: Storefront customization strategies
menu_title: Storefront customization strategies
menu_order: 
github_link: architecture/storefront_customization.md

---

<h2>店舗カスタマイズストラテジー</h2>

Magentoがサポートする店舗カスタマイズの範囲について概要を述べます。
この範囲はMagentoディフォルト店舗設定への小さな追加を含む最もシンプルなカスタマイズからMagento提供のHTMLとCSSの完全変更までを網羅しています。

これら4レベルの可能な店舗カスタマイズは複雑さの順に並べられています。

<h3>Magento提供のCSS拡張</h3>
MagentoはディフォルトのテームとLESSベースCSSセットのスタイルを提供します。CSSのみ使用することで実質的に店舗を変更することができます。この簡素な手法は限られた予算のプロジェクトに適しているかもしれないですし、サイトに異なるスキンを作成する開発者が興味を持つかもしれません。小ビジネスはこの店舗カスタマイズにデフォルト値を拡張するためにサードパーティの作成したテーマをMagento Connectから購入して手順に入ります。

<h3>PHTMLテンプレートファイル変更</h3>
ディフォルトのCSSを拡張することに加えて、異なるHTMLマークアップを生成することができます。例えば、欠けたCSSのクラス名を追加しなければならないかもしれませんし、追加の`<div>`タグを視覚効果を得るために追記しなければならないかもしれません。JavaScriptを駆使して異なるHTMLマークアップを必要とするかもしれません。この変更は単純にMagento CSSの拡張より用件が厳しいかもしれませんが、以前小さなプロジェクトの少人数チームの範疇内です。

<h3>Magento提供のCSSの変更</h3>
Magentoにより提供されたディフォルトのCSSを編集するより、ディフォルト店舗CSSコードを自身のものに変更することになるかもしれません。この手法はプロジェクトをMagento提供のCSSを紐付けることがなくなりますが、プロジェクト開発と統合にはさらに大きな負荷がかかります。さらにMagentoから提供されてない別のCSSツールや技術の使用を可能にします。パートナーで自身のCSSライブラリのセットを作成した方はそのライブラリを異なる顧客のプロジェクトに再利用できます。（これらのユニークなライブラリはパートナーを市場の他の者から区別することになるかも知れません。）

CSSファイルを変更するのに加えて、多少HTMLとJavaScriptを変更する必要があるかもしれません。


<h3>Magento提供のCSS,HTML,JavaScriptの変更</h3>
ディフォルトのMagentoインストールが提供するものよりかなり違ったショッピング体験をお届けするのが課されたタスクです。しかしながら、将来にトレードオフとして追加の拡張機能をインストール環境に併合することが困難になるかもしれません。

<div class="bs-callout bs-callout-info" id="info">
  <p>注意: もしあなたが一貫してコードをタイプごとに区分けするという最善の手法を行えば、どのような店舗のカスタマイズも最適に行なえて今後のアップグレードを簡単なものにするでしょう。例えば、全てのHTMLをPHTMLファイルに収める。全てのJavaScriptをJavaScriptファイルに収める。</p>
</div>

<h3>関連するトピック</h3>

<a href="{{ site.gdeurl }}frontend-dev-guide/bk-frontend-dev-guide.html">フロントエンド開発者ガイド</a>


<a href="{{ site.gdeurl }}javascript-dev-guide/bk-javascript-dev-guide.html">JavaScript開発者ガイド</a>



