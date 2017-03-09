---
title: "エラー ： Web サーバーでデバッグを開始できません | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.http"
  - "vwd.nonadmin.error."
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "デバッガー, Web アプリケーション エラー"
  - "デバッグ [Visual Studio], エラー"
  - "デバッグ (ASP.NET Web アプリケーションを), 不可 (エラーのデバッグ開始の)"
  - "エラー [デバッガー], デバッグを開始できない"
  - "HTTP サーバー, デバッグ (エラーを)"
  - "IIS, デバッグ (DLL を)"
  - "リモート デバッグ, エラー"
  - "セキュリティ [デバッガー], Web アプリケーション"
  - "セキュリティ設定, チェック (既定の Web サイトを)"
  - "不可 (エラーのデバッグ開始の)"
ms.assetid: f62e378a-3a99-4f78-9d97-8bb63a4da181
caps.latest.revision: 31
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# エラー ： Web サーバーでデバッグを開始できません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Web サーバーで実行されている ASP.NET アプリケーションをデバッグしようとする場合、次のエラー メッセージが表示されることがあります。Web サーバーでデバッグを開始できません。  
  
 ほとんどの場合、このエラーは、IIS が正しく構成されていない場合に発生します。  
  
##  <a name="vxtbshttpservererrorsthingstocheck"></a> IIS が正しく構成されていることを確認します。  
 MVC 5 アプリの IIS 8 へのデプロイについて詳しくは、「[IIS への発行](https://docs.asp.net/en/latest/publishing/iis.html)」をご覧ください。  
  
 IIS7.5 へのデプロイについて詳しくは、「[リモートの IIS 7.5 コンピューター上の ASP.NET のリモート デバッグ](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)」をご覧ください。  
  
##  <a name="vxtbshttpservererrorswebapplicationsonremoteservers"></a> Visual Studio リモート ツールがインストールされていることを確認します。  
 リモート Web サーバーでデバッグする場合は、Visual Studio リモート ツールをインストールする必要があります。 リモート ツールのダウンロードとインストールについて詳しくは、「[リモート デバッグ](../debugger/remote-debugging.md)」をご覧ください。  
  
##  <a name="vxtbshttpservererrorsanchor2"></a> ASP.NET がインストールされていることを確認します。  
 **IIS 8**  
  
 IIS 8 では、IIS の一部として ASP.NET をインストールします。  
  
1.  **\[サーバー マネージャー\]** タイルで、**\[ダッシュボード\]** を選択し、**\[役割と機能の追加\]** をクリックします。  
  
2.  **\[インストールの種類\]** ページで、**\[役割ベースのインストールか機能ベースのインストール\]** を選択して、**\[次へ\]** をクリックします。  
  
3.  **\[ターゲット サーバーの選択\]** ページで、**\[サーバー プールからサーバーを選択する\]** を選択し、使用するサーバーを選択し、**\[次へ\]** をクリックします。  
  
4.  **\[サーバーの役割の選択\]** ページで、**\[Web サーバー \(IIS\)\]** を選択して、**\[次へ\]** をクリックします。  
  
5.  **\[機能の選択\]** ページで **\[次へ\]** をクリックします。  
  
6.  **\[Web サーバーの役割 \(IIS\)\]** ページで **\[次へ\]** をクリックします。  
  
7.  **\[役割サービスの選択\]** ページで、既定でインストールされている事前選択された役割サービスを確認し、**\[アプリケーション サーバー\]** ノードを展開してから **\[.NET Framework 4.5\]** ノードを展開し、**\[ASP.NET 4.5\]** を選択します  \(.NET 3.5 をインストールした場合は、**ASP.NET 3.5** も選択します\)。  
  
8.  **\[インストール オプションの確認\]** ページで、**\[インストール\]** をクリックします。  
  
9. **\[インストールの進行状況\]** ページで、Web サーバー \(IIS\) 役割と必要な役割サービスのインストールが正常に完了していることを確認し、**\[閉じる\]** をクリックします。  
  
 **IIS 7.5 以前**  
  
 IIS 7.5 以前の場合、コマンド プロンプト ウィンドウで、次のコマンドを実行します。  
  
```  
systemroot\Microsoft.NET\Framework\ versionNumber \aspnet_regiis -i   
```  
  
## 基本的なトラブルシューティング  
 ASP.NET アプリケーションが正しくデプロイされていることを確認するために考慮できる点をいくつか示します。  
  
## ブラウザーで localhost ページを表示します  
 IIS が正しくインストールされていない場合、ブラウザーに `http://localhost` を入力するとエラーが表示されます。  
  
## ブラウザーで Web ページを表示します  
 Web ブラウザーを起動し、デバッグするページの URL を入力します \(例: `http://localhost/MyWebApplication`\)。 IIS が正しく構成されていないか、ASP.NET アプリケーションが正しくデプロイされていない場合、IIS のセットアップと ASP.NET のデプロイを修正するためのエラーが表示されます。  
  
## サーバー上に基本的な ASP.NET アプリケーションを作成します  
 サーバー上に基本的な ASP.NET アプリケーションをローカルで作成し、デバッグします。  
  
## IP アドレスのみを使用している場合は、認証エラーを解決します  
 Web サーバーのデバッグには、NTLM 認証が必要です。 既定では、IP アドレスはインターネットの一部と見なされ、インターネット上では NTLM 認証が行われません。 この問題を解決するため、リモート コンピューターの名前を指定することができます。  
  
##  <a name="vxtbshttpservererrorsmanuallyattaching"></a> 手動でプロセスにアタッチします  
 デバッグを行うとエラー メッセージがまだ表示される場合は、手動でプロセスにアタッチすることによってアプリケーションのデバッグを行います。  
  
-   デバッグを行わずにアプリケーションを起動します。**\[デバッグ\]** メニューの **\[デバッグなしで開始\]** をクリックします。  
  
-   **\[デバッグ\]、\[プロセスにアタッチ\]** の順にクリックします。  ウィンドウが表示されたら、**\[全ユーザーのプロセスを表示する\]** を有効にします。  
  
-   適切なプロセスを探し、それにアタッチします。 MVC 5 以前の ASP.NET アプリの場合、プロセスは w3wp.exe です。 MVC 5 の場合、「[IIS への発行](https://docs.asp.net/en/latest/publishing/iis.html)」をご覧ください。  
  
## 参照  
 [Web アプリケーションのデバッグ : エラーおよびトラブルシューティング](../debugger/debugging-web-applications-errors-and-troubleshooting.md)