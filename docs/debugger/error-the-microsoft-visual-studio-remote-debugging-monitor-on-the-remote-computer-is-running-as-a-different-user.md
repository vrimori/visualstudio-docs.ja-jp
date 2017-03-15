---
title: "エラー : リモート コンピューター上の Microsoft Visual Studio リモート デバッグ モニターは、別のユーザーで実行しています。 | Microsoft Docs"
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
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "anyuser オプション"
  - "-anyuser オプション"
  - "msvsmon.exe"
  - "リモート デバッグ モニター"
  - "リモート デバッグ, リモート デバッグ モニター"
ms.assetid: e5b18734-2daf-4c58-b5de-24ae1295703e
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# エラー : リモート コンピューター上の Microsoft Visual Studio リモート デバッグ モニターは、別のユーザーで実行しています。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

リモート デバッグを行おうとすると、次のエラー メッセージが表示される場合があります。  
  
 リモート コンピューター上の Microsoft Visual Studio リモート デバッグ モニターは、別のユーザーで実行しています。  
  
## 原因  
 このメッセージは、認証なしモードでのデバッグ中に、msvsmon を起動したユーザーが Visual Studio を実行中のユーザーと一致しない場合に発生します。  
  
## 解決方法  
 最も安全で適切な解決策は、Visual Studio と同じユーザー アカウントでリモート デバッグ モニター \(msvsmon.exe\) を実行することです。  これができない場合は、リモート デバッグ モニターの **\[オプション\]** ダイアログ ボックスの **\[すべてのユーザーにデバッグを許可する\]** をオンにして他のアカウントでリモート デバッグ モニターを実行します。  
  
> [!CAUTION]
>  他のユーザーに接続する許可を与えると、誤ったリモート デバッグ セッションに接続してしまう可能性があります。  **認証なし**モードでのデバッグは決して安全ではなく、使用には注意が必要です。  
  
 詳細については、「[リモート デバッグ モニターの起動](../Topic/Start%20%20the%20Remote%20Debugging%20Monitor.md)」を参照してください。  
  
## 参照  
 [リモート デバッグ エラーとトラブルシューティング](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [リモート デバッグ](../debugger/remote-debugging.md)