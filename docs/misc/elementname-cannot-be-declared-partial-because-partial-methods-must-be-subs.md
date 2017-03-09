---
title: "部分メソッドは Sub である必要があるため、&#39;&lt;elementname&gt;&#39; を &#39;Partial&#39; として宣言することはできません。 | Microsoft Docs"
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
  - "vbc31437"
  - "bc31437"
helpviewer_keywords: 
  - "BC31437"
ms.assetid: 31ca12ab-2c26-4907-a253-e7c57bb4f34b
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 部分メソッドは Sub である必要があるため、&#39;&lt;elementname&gt;&#39; を &#39;Partial&#39; として宣言することはできません。
`Sub` プロシージャのみ、部分メソッドとして宣言できます。 たとえば、次のコードでは `partialMethod` が関数であるのでこのエラーが発生します。  
  
```  
' Partial Private Function partialMethod(ByVal n As Integer) As Integer ' End Function  
```  
  
 **エラー ID:** BC31437  
  
### このエラーを解決するには  
  
-   部分メソッドとして宣言しようとしているものを `Sub` に変換します。  
  
-   この場合は、部分メソッドを使用しないでください。  
  
## 参照  
 [Partial Methods](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)   
 [Sub Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/sub-procedures)