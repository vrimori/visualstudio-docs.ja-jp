---
title: "Windows ストア アプリ用コンテンツのプリフェッチ | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
ms.assetid: b4481fef-3ebf-4f7d-9748-d43821a0ebac
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Windows ストア アプリ用コンテンツのプリフェッチ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Windows ストア アプリの応答性を高めるために、Web ページやイメージなどの一部の Web コンテンツを Windows がアプリの [WinINet](http://msdn.microsoft.com/ja-jp/0a06f2af-957a-4dff-a8cc-187370181b5c) [WinINet](http://msdn.microsoft.com/library/aa383630.aspx)キャッシュにプリロードするように要求することができます。この機能をプリフェッチと呼びます。これは起動時に使用されるコンテンツに特に効果的ですが、他の頻繁に使用するコンテンツをプリフェッチすることもできます。[Windows.Networking.BackgroundTransfer.ContentPrefetcher](http://msdn.microsoft.com/library/windows/apps/windows.networking.backgroundtransfer.contentprefetcher.aspx) クラスのメソッドで、プリロードするコンテンツの URI を指定できます。アプリに ContentPrefetcher 機能を追加する方法の例については、Windows SDK の「[Content prefetch sample \(コンテンツのプリフェッチの例\)](http://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309)」を参照してください。  
  
 Windows は、プリフェッチをする必要がある場合およびダウンロードするリソースを決定するためにヒューリスティックを使用します。このヒューリスティックでは、システム ネットワークおよび電力条件、ユーザー アプリの使用履歴、および以前のプリフェッチの結果を考慮します。Visual Studio では、**Trigger Windows Store App Prefetch** コマンドを使用して、Windows が ContentPrefetcher ヒューリスティックを無視し、指定されたすべての Web コンテンツをプリロードするようにします。これは、既知の状態 \(読み込まれている、または読み込まれていない\) でプリフェッチするコンテンツでアプリの動作またはパフォーマンスをテストする場合に役立ちます。  
  
## ContentPrefetcher で指定されるリソースのプリロードを強制するには  
 この手順では、ContentPrefetcher 機能が既に設定されていて、アプリ プロジェクトでプリロードするコンテンツ URI が指定されていると仮定しています。指定されたリソースが新しいまたは変更されている場合にコンテンツのプリロードを強制するには、**Trigger Windows Store App Prefetch** コマンドを選択する前にアプリを開始および停止する必要があります。まず、アプリを実行して、URI を登録します。**Trigger Windows Store App Prefetch** コマンドによって、ContentPrefetcher がコンテンツをダウンロードし、キャッシュに追加するように強制されます。アプリの後続の実行で、コンテンツがプリロードされたと見なすことができます。  
  
1.  アプリを開始して、アプリでプリフェッチ コンテンツ URI を登録します。\[**デバッグ**\] メニューで、\[**デバッグの開始**\] をクリックします \(キーボード ショートカット: F5 キー\)。  
  
2.  \[**デバッグ**\] メニューで、\[**デバッグの停止**\] をクリックします \(キーボード ショートカット: Shift \+ F5 キー\)。  
  
3.  \[**デバッグ**\] メニューで、\[**その他のデバッグ ターゲット**\] をクリックし、\[**Windows ストア アプリ プリフェッチのトリガー**\] をクリックします。  
  
 プリフェチした Web リソースでアプリをデバッグ、テスト、または分析できるようになりました。  
  
> [!NOTE]
>  指定された Web コンテンツを追加または変更するたびにこの手順を繰り返します。  
  
## 参照  
 [ブログ投稿: Triggering Prefetch for Windows Store Apps in Visual Studio 2013 Update 2 \(Visual Studio 2013 Update 2 で Windows ストア アプリのプリフェッチをトリガーする\)](http://blogs.msdn.com/b/visualstudioalm/archive/2014/02/06/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2.aspx)