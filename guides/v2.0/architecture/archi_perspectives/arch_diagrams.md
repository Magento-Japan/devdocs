---
layout: default
group: arch-guide
subgroup: Architectural Basics
title: Architectural diagrams
menu_title: Architectural diagrams
menu_order: 1
github_link: architecture/archi_perspectives/arch_diagrams.md
redirect_from: /guides/v1.0/architecture/archi_perspectives/arch_diagrams.html
---

<h2 id="m2arch-whatis-overview">アーキテクチャー図</h2>
Magentoをもっと知るあなたの役割と目的によって、Magentoのアーキテクチャーの見方には複数の異なる見方があります。例えば、新しいモジュールを作成したいまたは既存モジュールをカスタマイズしたい開発者はモジュール自体のアーキテクチャーを理解したいでしょうし、またそれがさらに大きな視点にMagentoフレームワークや他のコンポーネントとともに当てはまるのかを理解したいと思われます。しかしながら、小売店業者で早急>にオンライン店舗を作成したい人はコンポーネントの種類を上位レベルから見たいでしょうし、見た目、使用感、ユーザーが関わるコンポーネントを理解したい
でしょう。

<h3 id="archi-layers">アーキテクチャーレイヤー図</h3>

以下の図はMagentoのコンポーネントを表し、すべてのコンポーネントのレイヤーまたはTierを表し、さらにMagentoフレームワーク、サードパーティライブラリ、サポートするデータベース、そしてその他の技術を表しています。

<p><img src="{{ site.baseurl }}common/images/archi_diagrams_layers_alt4.jpg" alt="Magento architecture layers"></p>

<h3 id="archi-topo">トポロジ</h3>

トポロジ図は典型的実装を図解します。

[//]: # "The technologies that are required, and must be implemented, are indicated; be aware that this is the components of Magento, and shows the "layer" or tiers, for each component, including the Magento framework, 3rd party libraries, the supported database, and other technologies."

*図は今後のスプリントで公開されます*

<h3 id="archi-module">モジュール図</h3>

モジュール図は典型的Magentoモジュール内の複数のコンポーネントと依存性のあるものを図解します。 

*図は今後のスプリントで公開されます*

<h3 id="archi-builder">オンライン店舗図</h3>

以下の図はオンライン店舗かアプリケーションを作成したいユーザーの観点を表したものです。

*図は今後のスプリントで公開されます*


<h3 id="m2arch-related">関連するトピック</h3>

* <a href="{{ site.gdeurl }}architecture/arch_asmodsys.html">モジュラーシステムとしてのMagento</a>
* <a href="{{ site.gdeurl }}architecture/archi_perspectives/ALayers_intro.html">アーキテクチャーレイヤー概要</a>

