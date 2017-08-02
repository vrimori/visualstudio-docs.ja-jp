---
title: "Visual Studio からの Windows ストア アプリの配置 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: ef3a0f36-bfc9-4ca0-aa61-18261f619bff
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Visual Studio からの Windows ストア アプリの配置
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

![Windows のみに適用されます](~/docs/debugger/media/windows_only_content.png "windows\_only\_content")  
  
 Visual Studio の配置機能では、Visual Studio を使ってターゲット デバイスに作成した Windows ストア アプリをビルドおよび登録します。 アプリの厳密な登録方法は、ターゲット デバイスがローカルかリモートかによって違います。  
  
-   ターゲットがローカルの Visual Studio コンピューターの場合、Visual Studio はアプリをビルド フォルダーから登録します。  
  
-   ターゲットがリモート デバイスの場合、Visual Studio は必要なファイルをリモート コンピューターにコピーしてから、そのデバイス上でアプリを登録します。  
  
 \[**デバッグの開始**\] オプション \(キーボード: F5\) または \[**デバッグなしで開始**\] オプション \(キーボード: CTRL \+ F5\) を使用して Visual Studio からアプリをデバッグする場合、展開は自動的に行われます。 アプリを手動で配置することも可能です。 次のシナリオでは、手動の配置は有効です。  
  
-   ローカル コンピューターまたはリモート コンピューターで行う臨時のテスト。  
  
-   デバッグ対象のアプリを起動するためのアプリを配置する場合。  
  
-   別のアプリまたはメソッドによって起動される、デバッグ対象のアプリを配置します。  
  
##  <a name="BKMK_In_this_topic"></a> このトピックの内容  
 このトピックでは、次について説明します。  
  
 [Windows ストア アプリの配置方法](#BKMK_How_to_deploy_a_Windows_Store_app)  
  
 [リモート デバイスの指定方法](#BKMK_How_to_specify_a_remote_device)  
  
 [配置オプション](#BKMK_Deployment_options)  
  
##  <a name="BKMK_How_to_deploy_a_Windows_Store_app"></a> Windows ストア アプリの配置方法  
 アプリを手動で配置する手順はシンプルです。  
  
1.  リモート デバイスへ配置する場合は、アプリのスタートアップ プロジェクトのプロパティ プロジェクト ページに、デバイスの名前または IP アドレスを指定します。 \(指定するステップはこのトピック内で後述\)。  
  
2.  デバッガーの Visual Studio ツールバーで、**\[デバッグの開始\]** ボタンの横のドロップダウン リストから配置ターゲットを選択します。  
  
     ![ローカル コンピューターでの実行](../debugger/media/vsrun_f5_local.png "VSRUN\_F5\_Local")  
  
3.  **\[ビルド\]** メニューで **\[配置\]** を選択  
  
##  <a name="BKMK_How_to_specify_a_remote_device"></a> リモート デバイスの指定方法  
 **必要条件**  
  
 アプリをリモート デバイスに配置するには  
  
-   リモート デバイスに開発者ライセンスがインストールされている必要があります。  
  
-   リモート デバイスには、Visual Studio リモート ツールをインストールする必要があり、リモート デバッグ モニターが動作している必要があります。  
  
     配置では、リモート デバッガーのネットワーク チャネルを使用して、アプリのファイルをリモート デバイスに送信します。  
  
#### リモート デバイスを指定するには  
  
1.  スタートアップ プロジェクトのデバッグ プロパティ ページで、リモートの配置ターゲットの名前または IP アドレスを指定します。  
  
2.  デバッグ プロパティ ページを開くには、ソリューション エクスプローラーでプロジェクトを選択してから、ショートカット メニューで **\[プロパティ\]** を選択します。  
  
3.  次に、プロパティ ページ ウィンドウで **\[デバッグ\]** ノードを選択します。  
  
4.  リモート デバイスの名前または IP アドレスを入力するか、**\[リモート デバッガー接続の選択\]** ダイアログ ボックスからデバイスを選択します。  
  
     ![&#91;Select Remote Debugger Connection&#93; &#40;リモート デバッガーの接続の選択&#41; ダイアログ ボックス](~/docs/debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN\_SelectRemoteDebuggerDlg")  
  
     **\[リモート デバッガー接続の選択\]** ダイアログ ボックスは、ローカル ネットワークのサブネットにあるデバイスと、Visual Studio コンピューターにイーサネット ケーブルで直接接続されているデバイスを表示します。  
  
 **JavaScript または Visual C\+\+ のプロジェクト ページにあるリモート デバイスを指定**  
  
 ![リモート デバッグ用の C&#43;&#43; プロジェクト プロパティ](~/docs/debugger/media/vsrun_cpp_projprop_remote.png "VSRUN\_CPP\_ProjProp\_Remote")  
  
1.  **\[起動するデバッガー\]** ボックスの一覧の **\[リモート デバッガー\]** をクリックします。  
  
2.  **\[コンピューター名\]** ボックスのリモート デバイスにネットワーク名を入力します。 あるいはボックス内の下向き矢印をクリックして、\[リモート デバッガー接続の選択\] ダイアログ ボックスからデバイスを選択します。  
  
 **Visual C\# および Visual Basic のプロジェクト ページにあるリモート デバイスを指定**  
  
 ![リモート デバッグ用のマネージ プロジェクト プロパティ](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN\_Managed\_ProjProp\_Remote")  
  
1.  **\[ターゲット デバイス\]** ボックスの一覧の **\[リモート コンピューター\]** をクリックします。  
  
2.  リモート デバイスのネットワーク名を **\[リモート コンピューター\]** ボックスに入力するか、**\[検索\]** をクリックし、**\[リモート デバッガー接続の選択\]** ダイアログ ボックスでデバイスを選択します。  
  
##  <a name="BKMK_Deployment_options"></a> 配置オプション  
 次の配置オプションを、スタートアップ プロジェクトのデバッグ プロパティ ページに設定できます。  
  
 **ネットワーク ループバックの許可**  
 セキュリティ上の理由から、標準的な方法でインストールされた [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] アプリは、インストール先のデバイスに対してネットワーク呼び出しを行うことはできません。 既定では、Visual Studio による配置では、配置されたアプリに対するこの規則の適用は免除されます。 この免除によって、1 台のコンピューター上で通信プロシージャをテストできます。 アプリを [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] に送信する前に、アプリを適用除外せずにテストする必要があります。  
  
 アプリからネットワーク ループバックの適用除外を削除するには  
  
-   C\# および VB のデバッグ プロパティ ページで、**\[ネットワーク ループバックの許可\]** チェック ボックスをクリアします。  
  
-   JavaScript およびデバッグ プロパティ ページで、**\[ネットワーク ループバックの許可\]** の値を **\[いいえ\]** に設定します。  
  
 **起動しない。ただし開始した場合にはコードをデバッグ \(C\# および VB\) \/ アプリケーションを起動 \(JavaScript および C\+\+\)**  
 アプリが起動した場合はデバッグ セッションを自動駅に開始するように、配置を構成するには  
  
-   C\# および VB のデバッグ プロパティ ページで、**\[起動しないが、開始時にコードをデバッグ\]** チェック ボックスをオンにします。  
  
-   JavaScript およびデバッグ プロパティ ページで、**\[アプリケーションの起動\]** の値を **\[はい\]** に設定します。  
  
## 参照  
 [Visual Studio からのアプリの実行](../debugger/run-store-apps-from-visual-studio.md)