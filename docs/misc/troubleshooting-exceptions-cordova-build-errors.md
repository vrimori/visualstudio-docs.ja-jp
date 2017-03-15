---
title: "例外のトラブルシューティング: Cordova ビルド エラー | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BLD102"
  - "BLD10205"
  - "BLD301"
  - "BLD401"
  - "BLDErr_Build_NodeMissing"
  - "BLDErr_BLD_Win8Required"
ms.assetid: 781c09e3-0704-4b30-9230-036cbdb2dff9
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
---
# 例外のトラブルシューティング: Cordova ビルド エラー
このトピックでは、Visual Studio Tools for Apache Cordova を使用する際に表示される可能性のある、より一般的なエラー メッセージの一部を説明します。  
  
-   [MSBUILD: cordova ビルド エラー BLD102: 該当するファイルまたはディレクトリがありません 'config.xml'](#BLD102)  
  
-   [MSBUILD: cordova ビルド エラー BLD301: iOS リモート ビルド エージェントが構成されていません](#BLD301)  
  
-   [MSBUILD: cordova ビルド エラー BLD401: モジュール &lt;modulename&gt; が見つかりませんでした](#BLD401)  
  
-   [MSBUILD: cordova ビルド エラー BLD10205: Android ターゲットをインストールしてください](#BLD10205)  
  
-   [BLDErr_Build_NodeMissing Node.js 実行可能ファイルのパスを特定できません。](#BLDErr_Build_NodeMissing)  
  
-   [BLDErr_Build_Win8Required](#BLDErr_Build_Win8Required)  
  
 Cordova アプリで発生したエラーのトラブルシューティングに役立つ全般的な情報が必要な場合は、「[Resolving build errors](https://taco.visualstudio.com/en-us/docs/resolving-build-errors/)」 \(ビルド エラーの解決\) を参照してください。  
  
##  <a name="BLD102"></a> MSBUILD: cordova ビルド エラー BLD102: 該当するファイルまたはディレクトリがありません 'config.xml'  
 このエラーが表示された場合は、プロジェクトのプロジェクト ルートに config.xml ファイルが含まれていることと、プロジェクトがネットワーク共有上に存在するのではなく、ローカル コンピューター上にあることを確認します。  
  
 詳しくは、この「[StackOverflow の投稿](http://stackoverflow.com/questions/27134007/new-cordova-project-gives-the-error-bld00102-no-such-file-or-directory-confi)」をご覧ください。  
  
##  <a name="BLD301"></a> MSBUILD: cordova ビルド エラー BLD301: iOS リモート ビルド エージェントが構成されていません  
 エラー文字列の全文は次のようになります。  
  
-   MSBUILD: cordova ビルド エラー BLD301: iOS リモート ビルド エージェントが構成されていません。 \[ツール\] \> \[オプション\] \> \[Apache Cordova 用ツール\] \> \[リモート エージェントの構成\] をクリックしてビルド エージェントを構成してください。 詳細と代替手段については、http:\/\/go.microsoft.com\/fwlink\/?LinkID\=511904 を参照してください。  
  
 iOS 用 remotebuild エージェントのインストールと構成については、「[iOS セットアップ ガイド](http://taco.visualstudio.com/en-us/docs/ios-guide/)」をご覧ください。  
  
##  <a name="BLD401"></a> MSBUILD: cordova ビルド エラー BLD401: モジュール \<modulename\> が見つかりませんでした  
 エラー文字列の全文は次のようになります。  
  
-   MSBUILD: cordova ビルド エラー BLD401: エラー : BLD00401 : モジュール \<modulename\> が見つかりませんでした。 \[ツール\] \-\-\> \[オプション\] \-\-\> \[Apache Cordova 用ツール\] \-\-\> \[Cordova ツール\] \-\-\> \[Cordova キャッシュのクリア\] と移動し、ビルドを再試行してください。  
  
 キャッシュをクリアし、vs\-tac を再インストールしなければならない場合があります。 詳しくは、「[vs\-tac の再インストール](http://taco.visualstudio.com/en-us/docs/configure-vs-tools-apache-cordova#vstac)」をご覧ください。  
  
 キャッシュをクリアしたら、プロジェクトのプラットフォーム フォルダーを削除します。 その後、もう一度ビルドを試みてください。  
  
##  <a name="BLD10205"></a> MSBUILD: cordova ビルド エラー BLD10205: Android ターゲットをインストールしてください  
 このエラーが発生する場合は、Android SDK Manager \(SDK Manager.exe\) を使用して、選んだターゲット デバイスに必要な依存関係をインストールしてください。  
  
 必要な API レベルおよび他の Android SDK コンポーネントについて詳しくは、「[手動による依存関係のインストール](http://taco.visualstudio.com/en-us/docs/configure-vs-tools-apache-cordova#ThirdParty)」をご覧ください。  
  
 Android SDK の検索に Visual Studio が使用している場所も確認する必要があります。 これを行うには、「[システム環境変数のオーバーライド](http://taco.visualstudio.com/en-us/docs/configure-vs-tools-apache-cordova#env-var)」をご覧ください。  
  
 ツールを使用するための適切なコンポーネントのインストールについて詳しくは、「[サード パーティ製ツール](http://taco.visualstudio.com/en-us/docs/install-vs-tools-apache-cordova#choose)」をご覧ください。  
  
##  <a name="BLDErr_Build_NodeMissing"></a> BLDErr\_Build\_NodeMissing Node.js 実行可能ファイルのパスを特定できません。  
 Node.js が既定以外の場所にインストールされている場合、Visual Studio が見つけられない可能性があります。 既定の場所に Node.js を再インストールします。 詳しくは、この「[StackOverflow の投稿](http://stackoverflow.com/questions/32203992/vs2015-cordova-apps-blderr-build-nodemissing)」および「[Node.js の安全な更新](http://taco.visualstudio.com/en-us/docs/change-node-version/)」に関するこの記事をご覧ください。  
  
##  <a name="BLDErr_Build_Win8Required"></a> BLDErr\_Build\_Win8Required  
 Visual Studio Tools for Apache Cordova を使用して作成されたアプリで Windows をターゲットにするには、Windows 8.1 が必要です。