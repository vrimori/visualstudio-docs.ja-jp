---
title: "&#39;Line&#39; ステートメントはサポートされていません (Smart Device/Visual Basic コンパイラ エラー) | Microsoft Docs"
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
  - "vbc30768"
  - "bc30768"
helpviewer_keywords: 
  - "BC30768"
ms.assetid: e7a17c77-06bb-4d33-966e-addb4f51caaf
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Line&#39; ステートメントはサポートされていません (Smart Device/Visual Basic コンパイラ エラー)
`Line` ステートメントはサポートされなくなりました。 通常、ファイル I\/O 機能は <xref:Microsoft.VisualBasic.FileSystem.LineInput%2A?displayProperty=fullName> として使用できますが、.NET Compact Framework のターゲット バージョンではサポートされていません。  
  
 **エラー ID:** BC30768  
  
### このエラーを解決するには  
  
-   ファイル アクセスを実行するには、<xref:System.IO> 名前空間で定義された関数を使用します。  
  
-   グラフィックス処理を行っている場合は、<xref:System.Drawing.Graphics.DrawLine%2A?displayProperty=fullName> を使用します。  
  
## 参照  
 <xref:System.IO>   
 <xref:System.Drawing>   
 [File Access with Visual Basic](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/file-access)