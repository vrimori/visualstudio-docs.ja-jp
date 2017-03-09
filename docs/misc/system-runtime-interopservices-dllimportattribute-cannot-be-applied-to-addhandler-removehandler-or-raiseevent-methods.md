---
title: "&#39;System.Runtime.InteropServices.DllImportAttribute&#39; は、&#39;AddHandler&#39;、&#39;RemoveHandler&#39; または &#39;RaiseEvent&#39; メソッドには適用できません | Microsoft Docs"
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
  - "bc31531"
  - "vbc31531"
helpviewer_keywords: 
  - "BC31531"
ms.assetid: 0ea3a16c-cfe0-4cb5-b740-358679272f8d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System.Runtime.InteropServices.DllImportAttribute&#39; は、&#39;AddHandler&#39;、&#39;RemoveHandler&#39; または &#39;RaiseEvent&#39; メソッドには適用できません
`DllImportAttribute` 属性が `AddHandler`、`RemoveHandler`、`RaiseEvent` のいずれかのメソッドの宣言に適用されました。 この属性は、空の `Function` または `Sub` でのみ使用できます。  
  
 **エラー ID:** BC31531  
  
### このエラーを解決するには  
  
-   メソッド宣言から `DllImportAttribute` 属性を削除します。  
  
## 参照  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler \- 削除](http://msdn.microsoft.com/ja-jp/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler \- 削除](http://msdn.microsoft.com/ja-jp/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [RaiseEvent \- 削除](http://msdn.microsoft.com/ja-jp/7f765da0-5491-40b6-9ed5-24c98f9daad9)