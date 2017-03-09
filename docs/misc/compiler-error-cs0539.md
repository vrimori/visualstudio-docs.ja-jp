---
title: "コンパイラ エラー CS0539 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0539"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0539"
ms.assetid: 41b8975c-abd1-4a36-98a4-8efa5fb0502a
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0539
明示的インターフェイス宣言の中の 'member' はインターフェイスのメンバーではありません  
  
 存在しない[インターフェイス](/dotnet/csharp/language-reference/keywords/interface) メンバーを明示的に宣言しようとしました。 宣言を削除するか、有効なインターフェイス メンバーを参照するように宣言を変更する必要があります。  
  
 次の例では CS0539 が生成されます。  
  
```  
// CS0539.cs namespace x { interface I { void m(); } public class clx : I { void I.x()   // CS0539 { } public static int Main() { return 0; } } }  
```