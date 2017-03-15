---
title: "内部エラーのため、メモリ情報を取得できませんでした | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrDiagnosticInfo_Memory"
ms.assetid: 1ba8f774-5858-438e-914e-99fddc9e5e7e
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 内部エラーのため、メモリ情報を取得できませんでした
`My.Computer.Info` オブジェクトのメモリ情報のプロパティの 1 つに対する呼び出しが失敗しました。  
  
### このエラーを解決するには  
  
-   `My.Computer.Info` オブジェクトのメモリ情報プロパティへの呼び出しの周囲に `Try...Catch` を追加します。  
  
## 参照  
 [My.Computer.Info Object](/dotnet/visual-basic/language-reference/objects/my-computer-info-object)   
 [Visual Basic での例外とエラー処理](http://msdn.microsoft.com/ja-jp/3e351e73-cf23-40ab-8b60-05794160529e)   
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)