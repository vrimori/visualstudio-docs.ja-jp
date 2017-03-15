---
title: "[デバッグ操作を停止しています] ダイアログ ボックス | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.stopnow"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "SQL"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "[デバッグ操作を停止しています] ダイアログ ボックス"
ms.assetid: ed7ef49d-e25f-4a4d-9396-9bc7b4143117
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# [デバッグ操作を停止しています] ダイアログ ボックス
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このダイアログ ボックスは、デバッガーがデバッグ セッションを停止しようとしているものの、セッションの停止に時間がかかる場合に表示されます。  デバッグ セッションの停止は通常、非常に速く行われ、このダイアログ ボックスは表示されません。  ただし、デバッグ中のすべてのプロセスからデタッチするのに余分な時間がかかることがあります。  セッションの停止に数分以上かかる場合 \(またはデタッチ エラーが発生した場合\) は、このダイアログ ボックスが表示されます。  この症状が頻繁に発生する場合は、内部に問題がある可能性があります。製品サポート サービスにお問い合わせください。  
  
 プロセスがデタッチし、このダイアログ ボックスが消えるのを待つか、**\[今すぐ停止\]** を使って強制的に即時終了します。  
  
 **\[今すぐ停止\]**  
 デバッグ セッションを直ちに終了する場合は、このボタンをクリックします。  **\[今すぐ停止\]** は、デバッグ中のプロセスをデタッチするのではなく、デバッグ セッションを終了します。  システム プロセスをデバッグしている場合は、これらのプロセスを **\[今すぐ停止\]** で終了すると、予想不可能な結果や望ましくない結果になることがあります。  
  
## 参照  
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [Detaching Programs](http://msdn.microsoft.com/ja-jp/f2c756c2-8079-474b-94c2-01c19a141a01)