---
title: "リモート コンピューターにアクセスしようとしたときに、DCOM エラーが発生しました。アクセスが拒否されました。 | Microsoft Docs"
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
  - "vs.debug.remote.dcom_access_denied"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
helpviewer_keywords: 
  - "DCOM, アクセス エラー"
  - "リモート DCOM アクセス拒否エラー"
  - "リモート デバッグ, DCOM エラー"
ms.assetid: 9d7dfc1b-9fe0-4f54-9c50-9c0e0f8358c5
caps.latest.revision: 27
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# リモート コンピューターにアクセスしようとしたときに、DCOM エラーが発生しました。アクセスが拒否されました。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

リモート デバッグでは、DCOM を使用して次のような状況でローカル コンピューターとリモート コンピューターとの間で通信します。  
  
-   **\[ツール\]\/\[オプション\]\/\[デバッグ\]** ページで、デバッガーが **\[ネイティブ互換モード\]** に設定されるか、または **\[マネージ互換モード\]** がオンに設定されている場合。  
  
-   マネージ C\+\+ \(C \+ \+\/CLI\) コードをデバッグする場合。  
  
-   Visual Studio 2013 で、**\[ツール\]\/\[オプション\]\/\[デバッグ\]** ページの **\[ネイティブのエディット コンティニュを有効にする\]** がオンになっている場合。  
  
-   一部のサード パーティのデバッグ シナリオ  
  
 このエラーが発生するのは、Visual Studio のプロセスが DCOM 経由でリモート デバッガープロセスに対して自己認証できない \(入力した資格情報が不十分と見なされた\) 場合です。 次のいずれかの回避策で問題を解決できることがあります。  
  
-   **\[ネイティブ互換モード\]** と **\[マネージ互換モード\]** をオフにします。  
  
-   Visual Studio 2013 で、**\[ネイティブのエディット コンティニュを有効にする\]** をオフにします。  
  
-   両方のコンピューターを再起動する。  
  
-   リモート デバッグで資格情報の入力が必要な場合は、資格情報の保存のチェック ボックスをオンにする。  
  
## 参照  
 [リモート デバッグ エラーとトラブルシューティング](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [リモート デバッグ](../debugger/remote-debugging.md)