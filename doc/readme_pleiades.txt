━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Pleiades
──────────────────────────────────────────────────
URL    : http://mergedoc.sourceforge.jp/
MAIL   : kashihara @ me.com
AUTHOR : Shinji Kashihara (柏原 真二)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Pleiades は Eclipse プラグイン日本語化プラグインです。
実行時にメモリ上で Eclipse 本体と多くのプラグインを日本語化します。

対応プラグイン一覧
http://sourceforge.jp/projects/mergedoc/wiki/Pleiades%E5%AF%BE%E5%BF%9CEclipse%E3%83%97%E3%83%A9%E3%82%B0%E3%82%A4%E3%83%B3%E4%B8%80%E8%A6%A7



謝辞
──────────────────────────────────────────────────

  プロジェクト・メンバー

    Shinji Kashihara、いがぴょん (IGA Tosiki)、ymoto、Hideki Yamane (Debian JP)

  次の方々に翻訳提供や協力をいただきました。感謝いたします。(敬称略、順不同)

    かぬ、kutakuta、orihalcon、ちんちろりん、You＆I、asachin、遊、manila、Holy、yuizumi、yamamoto、
    いずも、samu、a man、muimy、yuki358、Pepe、same、yujirockets、inaba、shuji_w6e、MON-80、yoshisan、
    takekazuomi

    CodeGear from Borland、エンバカデロ・テクノロジーズ (CodeGear)、NTT データビジネスブレインズ、
    キヤノンソフトウェア株式会社

    (c) 19-10 - Eclipse 3.5～3.8 以降スプラッシュ画像



特徴
──────────────────────────────────────────────────

  ・翻訳対象のプラグインやバージョン（Eclipse 本体含む）に依存しません。
  ・リソースが外部化されていないプラグインでも日本語化されます。
  ・対象プラグインのプロパティファイルやクラスファイルは書き換えません。
  ・言語パックを入れた場合、その部分に関しては言語パックが優先(*1)されます。
  ・JDK の標準 API Javadoc ホバーを日本語化します(*2)。
  ・ヘルプは日本語化されません。
  ・実際はプラグインではなく、AOP を利用した翻訳コンテナです。


  (*1) Pleiades は基本的に Eclipse.org が配布する言語パックをすべて取り込み済みですが、言語パックが
       持つ明らかにおかしいと思われる訳は修正しています。言語パックを入れた場合、それらの恩恵は受け
       られません。なお、言語パックをインストール済みでも優先したくない場合は、Eclipse の起動時に
       -nl en_us（これは Eclipse が持つオプションです）を指定することですべて Pleiades 側で訳されます。

  (*2) Eclipse 3.2以降、Pleiades 1.2.1 以降。jar に日本語の API 日本語ドキュメントを設定した場合のみ
      （自動的にデフォルトで日本語版の URL が設定されます）。Eclipse 3.2 では jar に設定した API
       ドキュメントをホバー表示できますが、ソースを添付していた場合はそれが優先されてしまいます。
       Pleiades はその優先度を逆転させています。JDK などのソース自体を日本語化したい場合は MergeDoc
       を使用する必要があります。



動作環境
──────────────────────────────────────────────────

  ・JRE 5 以上
  ・Eclipse 3.1 以上



インストール / アンインストール
──────────────────────────────────────────────────

  1. pleiades_x.x.x.zip を解凍し、plugins、features ディレクトリーを <ECLIPSE_HOME> ディレクトリーに
     コピー。

  2. eclipse.ini の最終行に以下の記述を追加。
     -javaagent:plugins/jp.sourceforge.mergedoc.pleiades/pleiades.jar
    （Windows 以外の場合は後述の Eclipse 起動オプション参照）

     (Eclipse 3.3 以降)
  3. Pleiades スプラッシュ画像を使う場合は
     eclipse.ini の 1、2 行目の -showsplash org.eclipse.platform を削除。

 ┌ 注意 ────────────────────────────────────────────┐
 │Pleiades を更新したり、他のプラグインを追加・更新した場合は必ず起動オプションに -clean を指定 │
 │して起動してください。Windows の場合は同梱している "eclipse.exe -clean.cmd" で -clean 起動でき│
 │ます。-clean 起動しないと、configuration の古いプラグイン情報が使用され、起動できなくなったり │
 │更新したプラグインが正常に動作しなくなったりします。                                          │
 └───────────────────────────────────────────────┘

  初回起動時は自動的に -clean モードで起動します。-clean での起動は、現在の環境に合わせて次回以降の
  実行速度を Pleiades が最適化しますが、通常よりかなり遅くなるため、-clean の常用は避けてください。
  -clean 起動の後、5～6 回 通常起動すると、不要な辞書をロードしなくなるため軽くなります。

  Windows の場合、デフォルトのフォントが Courier New 10 ポイントになっていますが ＭＳ ゴシック
  9 ポイントをオススメします。下記から設定できます。メニューから
  [ウィンドウ] - [設定] を開き、[一般] - [外観] - [色とフォント] の [基本] - [テキスト・フォント]
  で設定してください。


  Pleiades を一時的に無効にしたい場合は -javaagent 指定を除去してください。完全にアンインストールす
  る場合は、-javaagent 指定を除去し、以下のディレクトリを削除してください。

    plugins/jp.sourceforge.mergedoc.pleiades/
    features/jp.sourceforge.mergedoc.pleiades/
    configuration/jp.sourceforge.mergedoc.pleiades/

  上記の 3 つ目は Pleiades の構成やログが出力される <Pleiades configuration ディレクトリー> です。
  Linux、Mac OSX の場合、デフォルトでは下記になります。ただし config.ini の osgi.configuration.area
  を指定している場合は、それが優先されます。

    $HOME/.eclipse/jp.sourceforge.mergedoc.pleiades/<インストールパス名>/



FAQ
──────────────────────────────────────────────────

  Q. 起動しない / 起動しなくなった / 強制終了させたらおかしくなった(※)

	1. Eclipse 起動オプション -clean を指定して起動してみてください。
	2. configuration/jp.sourceforge.mergedoc.pleiades/ ディレクトリーを削除して起動してみてください。
	3. コマンドラインから起動し、出力されるエラーを確認してください。Windows の場合は eclipse.exe
	   ではなく eclipsec.exe を使用してください。<Pleiades configuration ディレクトリー>/pleiades.log、
	   <ワークスペース>/.metadata/.log も確認してみてください。

	※強制終了させた場合は、必ず -clean 起動してください。初回起動や -clean での起動はマシンによって
	  は数分かかる場合があります。


  Q. 起動はするけど、まったく日本語化されない

	1. Eclipse 実行環境が JRE 5 以上になっているか確認してください。メニューの
	   Help -> About Eclipse Platform -> Configuration Details に表示される -vm の値で確認できます。


  Q. なんかあんまり日本語化されない / ところどころ英語になってしまった

	1. Eclipse 起動オプション -clean を指定して起動してみてください。
	2. configuration/jp.sourceforge.mergedoc.pleiades/ ディレクトリーを削除して起動してみてください。


  Q. Pleiades を入れたら WTP のプロジェクト・エクスプローラーに動的 Web プロジェクトなどが表示されな
     くなってしまった

	1. ワーキング・セットの設定を開いてチェックを入れなおしてください。



Eclipse 起動オプション
──────────────────────────────────────────────────

  Pleiades を有効にするには、Eclipse の起動オプションに、-javaagent を追加してください。pleiades.jar
  へのパス指定は、Windows、Mac OS、Linux いずれの場合も、カレント・ディレクトリーからの相対パス、
  または絶対パスを指定してください。


  ◆方法 1: eclipse.ini 最終行に以下の指定を追加

    * Windows での設定例 (相対パス)

      -javaagent:plugins/jp.sourceforge.mergedoc.pleiades/pleiades.jar


    * Mac OS での設定例 (絶対パス)

      Mac OS では  eclipse.ini は Eclipse.app/Contents/MacOS/ にあります。
      また、後述の no.mnemonic オプションは自動的に有効になります。

      -javaagent:/Applications/eclipse/plugins/jp.sourceforge.mergedoc.pleiades/pleiades.jar


  ◆方法 2: 起動引数に直接 pleiades.jar を指定

    例）eclipse -vmargs -javaagent:plugins/jp.sourceforge.mergedoc.pleiades/pleiades.jar -Xms40m -Xmx256m

    * 起動引数に -vmargs を指定している場合は eclipse.ini の -vmargs は無効になるため、ヒープサイズ
      も指定してください。



Pleiades 起動オプション
──────────────────────────────────────────────────

  Pleiades のオプションは -javaagent 指定の末尾に指定します。複数のオプションを
  指定する場合はカンマで区切ってください。

    例）-javaagent:plugins/jp.sourceforge.mergedoc.pleiades/pleiades.jar=option,,,
                                                                        ~~~~~~~~~~

  default.splash

    Pleiades はスプラッシュ画像を変更します。Eclipse デフォルトのスプラッシュ画像を使用したい場合は
    このオプションを指定してください。

    Eclipse 3.3 以降、eclipse.ini にデフォルトで -showsplash org.eclipse.platform が指定されています
    が、この -showsplash は見かけ上の速度を上げるため、VM 起動前にスプラッシュを表示する Eclipse
    起動オプションです。つまり、Pleiades を使用しない場合、-showsplash を指定有無に関わらず、表示
    されるスプラッシュは同じです。Pleiades 側では VM 起動前の処理を制御できないため、default.splash
    オプションは Eclipse 起動オプションの -showsplash が未指定の場合のみ有効です。


  no.mnemonic

    メニューの "ファイル(F)" 末尾の (F) のようなニーモニックを表示しないようにします。Mac OS では
    自動的にこのオプションが有効になります。


  enabled.not.found.log

    訳が見つからなかった場合に、ログをプロパティー形式で
    configuration/jp.sourceforge.mergedoc.pleiades/translation-notfound.properties に出力します。
    ただし、-clean で起動しないとキャッシュされているものは出力されません。

    このプロパティーから訳したい行をコピーし、Pleiades の /conf/additions ディレクトリーに適当なファ
    イル名でプロパティー・ファイル (.properties) を作成することで、オリジナルの訳を追加することがで
    きます。


  log.level=debug

    ログ・レベルを指定します。指定しない場合のデフォルトは info です。指定できる値は、
    debug, info, warn, error, fatal のいずれかです。



PDE での利用
──────────────────────────────────────────────────

  PDE などから Eclipse アプリケーションを起動して Pleiades を有効にするには
  一旦起動して起動構成を作成後、起動構成ダイアログの [引数]タブ - [VM 引数] に
  以下を指定してください。

    -javaagent:plugins/jp.sourceforge.mergedoc.pleiades/pleiades.jar



最新 Integration Build の取得
──────────────────────────────────────────────────

  http://svn.sourceforge.jp/cgi-bin/viewcvs.cgi/trunk/Pleiades/build/?root=mergedoc



Pleiades を Eclipse プロジェクトとして zip からインポート
──────────────────────────────────────────────────

  [ファイル] - [インポート] - [既存プロジェクトをワークスペースに] で[アーカイブ・ファイルの選択] を
  チェックし pleiades_x.x.x-src.zip を選択してインポートしてください。



Pleiades を Eclipse プロジェクトとして SVN からチェックアウト
──────────────────────────────────────────────────

  http://sourceforge.jp/projects/mergedoc/wiki/Pleiades%E3%82%92Eclipse%E3%83%97%E3%83%AD%E3%82%B8%E3%82%A7%E3%82%AF%E3%83%88%E3%81%A8%E3%81%97%E3%81%A6%E3%83%81%E3%82%A7%E3%83%83%E3%82%AF%E3%82%A2%E3%82%A6%E3%83%88%E3%81%99%E3%82%8B



翻訳ポリシー
──────────────────────────────────────────────────

  こちらで策定しています。
  http://wiki.eclipse.org/%E7%BF%BB%E8%A8%B3%E3%83%AB%E3%83%BC%E3%83%AB



ライセンス
──────────────────────────────────────────────────

  Copyright (c) 2005- Shinji Kashihara. All rights reserved.

  This program and the accompanying materials except for /lib directory are
  made available under the terms of the Eclipse Public License v1.0 which
  accompanies this distribution, and is available at /epl-v10.html.

  This product includes software developed by
  The Apache Software Foundation (http://www.apache.org/) and
  Shigeru Chiba, Tokyo Institute of Technology
  (http://www.csg.is.titech.ac.jp/~chiba/javassist/).

  Please read the different license files present in the /lib directory of
  this distribution.



Pleiades の辞書について
──────────────────────────────────────────────────

Pleiades の辞書には eclipse.org によって配布されてきた下記の言語パックの訳が含まれています。なお、
これらの訳は Pleiades により修正されている部分があります。

- birt-1.0.1
- birt-2.1.1
- cdt.sdk-2.0.2
- cdt.sdk-3.1.1
- dtp-sdk_0.9.1
- emf-sdo-SDK-2.1.1
- emf-sdo-SDK-2.2.1
- GEF-ALL-3.1.1
- GEF-ALL-3.2
- GMF-sdk-1.0.1
- tptp.sdk-TPTP-3.3.0
- tptp.sdk-TPTP-4.0.1
- tptp.sdk-TPTP-4.2.0
- uml2-SDK-1.1.1
- uml2-SDK-2.0.1
- VE-SDK-1.1.0.1
- VE-SDK-1.2.1
- wtp-sdk-0.7.1
- wtp-sdk-1.5.0
- wtp-sdk-1.5.1
- eclipse-SDK-2.1.2.1
- eclipse-SDK-3.0.1
- eclipse-SDK-3.1.1a
- eclipse-SDK-3.2.0
- eclipse-SDK-3.2.1

また、これらの言語パックは以下の Copyright（有効年範囲省略）が含まれています。

# Copyright (c) Actuate Corporation.
# Copyright (c) IBM Corporation and others.
# Copyright (c) Intel Corporation and others.
# Copyright (c) Nokia and others.
# Copyright (c) QNX Software Systems and others.
# Copyright (c) Rational Software Corporation and others.
# Copyright (c) Scapa Technologies Limited and others
# Copyright (c) Texas Instruments Inc. and others.



変更履歴
──────────────────────────────────────────────────

readme_pleiades_changes.txt 参照。
