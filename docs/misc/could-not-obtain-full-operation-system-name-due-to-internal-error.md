---
title: "内部エラーのために完全な運用システム名を取得できませんでした | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrDiagnosticInfo_FullOSName"
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 内部エラーのために完全な運用システム名を取得できませんでした
内部エラーのために完全な運用システム名を取得できませんでした。 これは、現在のコンピューターに WMI が存在しないことが原因である場合があります。  
  
 `My.Computer.Info.OSFullName` プロパティの呼び出しに失敗しました。 このエラーの考えられる原因は、Windows Management Instrumentation \(WMI\) が、現在のコンピューターにインストールされていないことです。  
  
### このエラーを解決するには  
  
1.  `My.Computer.Info.OSFullName` プロパティの呼び出しの周囲に `Try...Catch` ブロックを追加します。  
  
2.  WMI およびそのインストール方法の詳細については、 にアクセスし、「Windows Management Instrumentation Core」を検索します。  
  
## 参照  
 [My.Computer.Info.OSFullName プロパティ](http://msdn.microsoft.com/ja-jp/b3b0fbd1-4dc5-428a-ad04-0d9fc9c2a9be)   
 [Visual Basic での例外とエラー処理](http://msdn.microsoft.com/ja-jp/3e351e73-cf23-40ab-8b60-05794160529e)   
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)