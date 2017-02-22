---
title: "方法 : ASP.NET プロセスの名前を見つける | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
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
helpviewer_keywords: 
  - "ASP.NET のデバッグ, ASP.NET プロセス"
  - "ASP.NET プロセス"
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 方法 : ASP.NET プロセスの名前を見つける
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

実行中の [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] アプリケーションにアタッチする場合、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] プロセスの名前を把握している必要があります。  
  
-   IIS 6.0 または IIS 7.0 を実行している場合、プロセスの名前は w3wp.exe です。  
  
-   6.0 よりも前のバージョンの IIS を実行している場合、プロセスの名前は aspnet\_wp.exe です。  
  
 [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)] またはそれ以降のバージョンを使用してビルドされたアプリケーションでは、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] コードはファイル システムに存在し、テスト サーバー WebDev.WebServer.exe の下で実行できます。  この場合、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] プロセスの代わりに WebDev.WebServer.exe にアタッチする必要があります。  ただし、これは、ローカル デバッグだけに当てはまります。  
  
 古いバージョンの ASP アプリケーションは、インプロセスで実行する場合、IIS プロセス inetinfo.exe 内で実行します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### プロジェクト コードがファイル システムと IIS のどちらに存在するかを判断するには  
  
1.  Visual Studio で、**ソリューション エクスプローラー**が開いていない場合は、開きます。  
  
2.  アプリケーション名を含む最上位のノードを選択します。  
  
3.  **\[プロパティ\]** ウィンドウのタイトルにファイル パスが含まれる場合、アプリケーション コードはファイル システムに存在します。  
  
     それ以外の場合は、**\[プロパティ\]** ウィンドウのタイトルに Web サイト名が含まれます。  
  
### アプリケーションが実行されている IIS のバージョンを判断するには  
  
1.  **\[管理ツール\]** を検索し、実行します。  オペレーティング システムによって異なりますが、**\[コントロール パネル\]** にアイコンがある場合や、**\[スタート\]** ボタンをクリックしたときにメニュー項目として表示される場合があります。  
  
     Windows XP の場合、**\[コントロール パネル\]** は、カテゴリの表示またはクラシック表示のいずれかで表示できます。  カテゴリの表示の場合、**\[クラシック表示に切り替える\]** または **\[パフォーマンスとメンテナンス\]** をクリックして、**\[管理ツール\]** アイコンを表示します。  
  
2.  **\[管理ツール\]** のインターネット インフォメーション サービスを実行します。  MMC ダイアログ ボックスが表示されます。  
  
3.  左側のペインに複数のコンピューターが表示される場合、アプリケーション コードが存在するコンピューターを選択します。  
  
4.  IIS のバージョンは、右側のペインの **\[バージョン\]** 列に表示されます。  
  
## 参照  
 [Prerequistes for Remote Debugging Web Applications \(方法 : リモート サーバーで Web アプリケーションをデバッグする\)](../debugger/prerequistes-for-remote-debugging-web-applications.md)   
 [システム要件](../debugger/aspnet-debugging-system-requirements.md)   
 [ASP.NET のデバッグの準備](../debugger/preparing-to-debug-aspnet.md)   
 [Web アプリケーションとスクリプトのデバッグ](../debugger/debugging-web-applications-and-script.md)