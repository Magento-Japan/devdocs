---
layout: default
group: arch-guide
subgroup: Architectural Basics
title: Technology stack
menu_title: Technology stack
menu_order: 2
github_link: architecture/tech-stack.md
redirect_from: /guides/v1.0/extension-dev-guide/tech-stack.html
---
<h2>Magento技術スタック</h2>

Magentoの高度モジュール化構造は以下のオープンソース技術を含みます:

スタックコンポーネントが含んでいるのは:

* PHP (5.5 and 5.6)

* Coding standards PSR-0 (オートローディングスタンダード), PSR-1 (基本コーディングスタンダード), and PSR-2 (コーディングスタイルガイド), PSR-3, PSR-4

* HTML5

* CSS3 (LESS CSS pre-processor)

* JQuery (プライマリーJavaScriptライブラリ)

* RequireJS (要求によってJavaScriptリソースをロードするのを助けるライブラリ)
* Third-party libraries (Zend Framework 1, Zend Framework 2, Symfony)

* Apache 2.2, 2.4

* Nginx 1.7


* MySQL 5.6
* Composer (PHPのための依存性管理パッケージ) 

オプションスタックコンポーネントが含むのは:

* Varnish (キャッシング)
* Redis (セッションのために使用またはページキャッシング)
* Solr (検索エンジン)


Magentoは併合、機能エリア、パフォーマンスのためのテストスクリプトを含む自動化テストスイートも提供します。コンポーネントはユニットテストフレームワークのPHPUnitと機能テストフレームワークのSeleniumを含みます。

このフレームワークは`Magento/mtf`に含まれています。更なる情報はMagentoテストフレームワークガイドを御覧ください。

<h2>関連するトピック</h2>
<a href="{{ site.gdeurl }}architecture/stack-basics.html">スタック基本</a>


<a href="{{ site.gdeurl }}architecture/archi_perspectives/ABasics_intro.html">アーキテクチャー基本</a>
