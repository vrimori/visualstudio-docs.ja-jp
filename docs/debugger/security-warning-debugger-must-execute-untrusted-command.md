---
title: "セキュリティ警告 : デバッガーは信頼されないコマンドを実行する必要があります | Microsoft Docs"
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
  - "vs.debug.sourceserver.securityalert"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: e5c004b3-b364-4098-ac98-770076ca9981
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# セキュリティ警告 : デバッガーは信頼されないコマンドを実行する必要があります
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ソース サーバーを使用している場合、この警告ダイアログ ボックスが表示されます。  デバッガーがソース コードを取得するために実行する必要のあるコマンドが、srcsvr.ini ファイルに含まれる、ソース サーバーに対して信頼できるコマンドの一覧に記載されていないことを示します。  このコマンドが有効な場合、srcsvr.ini ファイルに追加できます。  それ以外の場合は、そのコマンドを実行しないようにしてください。  詳細については、「[シンボルとソース コードの管理](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)」を参照してください。  
  
## メッセージ テキスト  
 ソース サーバーからソースを取得するために、この信頼されていないコマンドを実行します。  
  
 既知の信頼できる発信元からのシンボル ファイル \(\*.pdb\) でない場合、コマンドは無効であるか、または実行に危険が伴うおそれがあります。  
  
 このコマンドを実行しますか。  
  
## UIElement の一覧  
 \[テキスト ボックス\]  
 実行する .pdb ファイルからのコマンド。  
  
 Run  
 コマンドの実行を許可します。  
  
 \[実行しない\]  
 コマンドの実行およびソース サーバーからのファイルのダウンロードを停止します。  
  
## 参照  
 [シンボルとソース コードの管理](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [ソース サーバー](http://msdn.microsoft.com/library/windows/desktop/ms680641.aspx)