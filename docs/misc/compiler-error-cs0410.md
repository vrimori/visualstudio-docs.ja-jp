---
title: "コンパイラ エラー CS0410 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0410"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0410"
ms.assetid: a8b11042-9119-465e-abf6-235cbc7b8db5
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0410
適切なパラメーターおよび戻り値の型が指定された 'method' のオーバーロードはありません  
  
 このエラーは、パラメーターの型が無効な関数でデリゲートをインスタンス化しようとした場合に発生します。 デリゲートのパラメーターの型は、そのデリゲートに割り当てている関数と一致する必要があります。  
  
## 使用例  
 次の例では CS0410 が生成されます。  
  
```  
// CS0410.cs // compile with: /langversion:ISO-1 class Test { delegate void D(double d ); static void F(int i) { } static void Main() { D d = new D(F);  // CS0410 } }  
```