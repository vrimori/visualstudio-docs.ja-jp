---
title: "&#39;ReDim&#39; では最も右にある次元のみ変更できます | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrArray_TypeMismatch"
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;ReDim&#39; では最も右にある次元のみ変更できます
`ReDim` ステートメントが `Preserve` キーワードを使用して、最後のディメンションではない配列のディメンションを変更しようとしました。`Preserve` を使用すると、配列の最後のディメンションについてのみ、サイズを変更できます。 他のすべてのディメンションに対しては、既存の配列と同じサイズを指定する必要があります。  
  
### このエラーを解決するには  
  
-   `Preserve` キーワードを削除します。  
  
## 参照  
 [ビルド内にありません: Visual Basic の配列の概要](http://msdn.microsoft.com/ja-jp/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)   
 [ビルド内にありません: Visual Basic における多次元配列](http://msdn.microsoft.com/ja-jp/d92cad25-07e2-4d79-8ea4-ab269700f5de)   
 [ReDim Statement](/dotnet/visual-basic/language-reference/statements/redim-statement)   
 [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [保存 \- 削除](http://msdn.microsoft.com/ja-jp/91badeab-b4e0-48b6-92c9-9f0c8f995d81)