---
layout: default
group: arch-guide
subgroup: 
title: Security overview
menu_title: Security 
menu_order: 
github_link: architecture/security_intro.md
---

<h2 id="security_intro">セキュリティ概要</h2>
Magento 2.0 は以下のセキュリティ向上を含んでいます:



* <b>パスワード管理向上</b>. Magentoはパスワード管理に使われるハッシングアルゴリズム(SHA-256)を強化しました。 


* <b>エスケープされたデータをディフォルトにすることによってクロスサイトスクリプティング攻撃の防止を改善</b>。Magentoフレームワークはアウトプット内のデータをエスケープする制御する規定を採用しています。これらの規定はHTMLページ（HTML,JSON,JavaScript）とEメールのためのアウトプットをエスケープする能力を含みます。 可能な箇所で、エスケープはクライアントコードに対して可視化されます。 フロントエンドディベロッパーガイドの <a href="{{ site.gdeurl }}frontend-dev-guide/templates/template-security.html">Security measures against XSS attacks</a> を御覧ください。 

* <b>ファイルアクセスへの許可制限</b>。限定されたファイルアクセスをプロダクションとディベロッパーモードに設定が可能。この変更が生成されたファイル、静的ファイル、その他様々なMagentoで作られたファイルやディレクトリー（ログ、バックアップ、レポートを含む）のセキュリティーを強化します。インストールガイドの <a href="{{ site.gdeurl }}install-gde/install/file-system-perms.html"> Set file system ownership and permissions </a>を御覧ください。

	またMagentoはディベロッパーモードとプロダクションモードの間を変換できるCLIコマンドを提供します。このコマンドを使用してモードを変更する時、システムはファイルシステムのパーミッションを変更します。プロダクションモードでは、ディレクトリのパーミッションは750に、ファイルパーミッションは640に設定されます。ディベロッパーモードではディレクトリのパーミッションは770に、ファイルのパーミッションは660に設定されます。 
	
	(もちろんパーミッションはユーザーの必要に応じて変更する必要があります。例として、Magentoファイルシステムオーナーはファイルシステムの権限を所持してなければなりません。対照的に、ウェブサーバーユーザーは読み権限のみファイルシステムに必要で書き込み権限が幾つかのディレクトリに必要です（例えば'pub/media'）。そしてウェブサーバーユーザーは全てのMagentoファイルシステムに書き込み権限を持つべきではありません。更なる情報については、 <a href="{{ site.gdeurl }}install-gde/prereq/apache-user.html"> Create the magento file system owner</a>.)を御覧ください。

* <b>クリックジャッキング手法の防止改善</b>。Magentoはあなたのお店をX-Frameオプションズ HTTP リクエストヘッダを使うことによってクリックジャッキング攻撃から保護します。 更なる情報については, <a href="{{ site.gdeurl }}config-guide/secy/secy-xframe.html"> X-Frame-Options header</a>を御覧ください。

* <b>ディフォルトでない管理画面URLの使用</b>。ディフォルト管理画面のURLは特定画面に自動パスワード推測による攻撃を容易にします。この種の攻撃を防ぐためMagentoはディフォルトでランダムな管理画面URIを製品インストール時に生成します。CLIはもしパスワードをお忘れの時に見ることができるように提供されています。CLIをこのURIを変更するために使うことも可能です。ディフォルトでない管理画面のURIはサイトを安全にはしませんが、使うことによって更に大規模な自動化攻撃を防ぐことが出来ます。さらなる情報にはコンフィギュレーションガイドにある<a href="{{ site.gdeurl }}install-gde/install/cli/install-cli-adminurl.html"> Display or change the Admin URI</a> を御覧ください。 




<h2>関連するトピック</h2>
<a href="{{ site.gdeurl }}config-guide/bk-config-guide.html">Configuration Guide</a>



