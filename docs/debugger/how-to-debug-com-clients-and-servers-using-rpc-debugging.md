---
title: "方法 : RPC デバッグを使用して COM クライアントおよびサーバーをデバッグする | Microsoft Docs"
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
  - "vs.debug.com"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "COM クライアント, デバッグ"
  - "COM サーバー, デバッグ"
  - "COM, デバッグ"
  - "インプロセス リモート プロシージャ呼び出しのデバッグ"
  - "アウトプロセス リモート プロシージャ コールのデバッグ"
  - "リモート デバッグ, RPC (リモート プロシージャ コール)"
  - "RPC (リモート プロシージャ コール)"
  - "RPC (リモート プロシージャ コール), デバッグ"
  - "RPC (リモート プロシージャ コール), デバッグ (COM クライアントとサーバーを)"
ms.assetid: 3e8526c8-43b5-4b87-8e0d-b22c24f0a3ea
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 方法 : RPC デバッグを使用して COM クライアントおよびサーバーをデバッグする
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

リモート プロシージャ コール \(RPC: Remote Procedure Call\) デバッグを使用して、COM クライアント\/サーバー アプリケーションをデバッグできます。  このデバッグを行うには、あらかじめ RPC デバッグを有効にする必要があります。  RPC デバッグを有効にすると、ステップ実行でクライアントからサーバーを呼び出すときに、デバッガーがサーバーにアタッチし、コードのデバッグができるようになります。  デバッガーをアタッチすることにより、クライアントおよびサーバーのどちらのプロセスでも、デバッガーのすべての機能を使用できます。  
  
### RPC デバッグを有効にするには  
  
1.  **\[ツール\]** メニューの **\[オプション\]** をクリックします。  
  
2.  **\[オプション\]** ダイアログ ボックスで、**\[デバッグ\]** フォルダーを選択します。  
  
3.  **\[ネイティブ\]** をクリックします。  
  
4.  **\[RPC デバッグ\]** チェック ボックスをオンにします。  
  
    > [!NOTE]
    >  RPC 呼び出しをデバッグするには、管理者またはパワー ユーザーの権限が必要です。  
  
    > [!NOTE]
    >  Microsoft Windows Vista が実行されているリモート サーバーへの RPC ステップ実行は、そのリモート サーバーにネイティブ デバッガーがアタッチされている場合のみ機能します。  それ以外の場合、エラー メッセージが表示されることなく RPC 呼び出しが失敗します。  何らかの方法で RPC 呼び出しに成功したとしても、RPC 呼び出しへのステップ インは正常に機能しません。  
  
## 参照  
 [COM サーバーおよび COM コンテナーのデバッグ](../debugger/com-server-and-container-debugging.md)   
 [Visual Studio でのデバッグ](../debugger/debugging-in-visual-studio.md)