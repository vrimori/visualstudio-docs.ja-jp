---
title: "マウスが存在しません | Microsoft Docs"
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
  - "vbrMouse_NoMouseIsPresent"
ms.assetid: 4472fd57-4217-4463-9d3c-dc4a8fe88f1b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# マウスが存在しません
`My.Computer.Mouse` オブジェクトのいずれかのプロパティが呼び出されましたが、コンピューターにマウスが接続されていないか、マウス ポートが取り付けられていません。  
  
### このエラーを解決するには  
  
-   `My.Computer.Mouse` オブジェクトのプロパティの呼び出しを、`Try...Catch` ブロックで囲みます。  
  
     または  
  
-   マウスをコンピューターに取り付けます。  
  
## 参照  
 [My.Computer.Mouse Object](/dotnet/visual-basic/language-reference/objects/my-computer-mouse-object)   
 [Visual Basic での例外とエラー処理](http://msdn.microsoft.com/ja-jp/3e351e73-cf23-40ab-8b60-05794160529e)   
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)