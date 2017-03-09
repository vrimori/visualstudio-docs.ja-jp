---
title: "遅延バインディング操作を式ツリーに変換することはできません | Microsoft Docs"
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
  - "vbc36604"
  - "bc36604"
helpviewer_keywords: 
  - "BC36604"
ms.assetid: 6fd66d12-8c99-46e0-9095-fe1b29fd2692
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 遅延バインディング操作を式ツリーに変換することはできません
遅延バインディング操作を式ツリーに変換しようとしました。 これは有効ではありません。 たとえば、次のコードでは、このエラーが発生します。  
  
```vb#  
Option Strict Off Module Module1 Sub Main() '' Not valid. ' Test(Function(someInstance) someInstance.SomeProperty) End Sub Sub Test(ByVal ex As Expressions.Expression(Of Func(Of Object, Object))) End Sub End Module  
```  
  
 **エラー ID:** BC36604  
  
## 参照  
 [Early and Late Binding](/dotnet/visual-basic/programming-guide/language-features/early-late-binding/early-and-late-binding)   
 [ビルド内にありません: LINQ の式ツリー](http://msdn.microsoft.com/ja-jp/1a2e8e74-4bbc-45ab-9a46-2b6cfce3bcb2)