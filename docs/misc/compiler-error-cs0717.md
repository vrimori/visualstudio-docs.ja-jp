---
title: "コンパイラ エラー CS0717 | Microsoft Docs"
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
  - "CS0717"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0717"
ms.assetid: 1976e82a-d048-4f13-a95a-a7f4e3cd7038
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0717
'static class': 静的クラスは、制約として使用することはできません  
  
 静的クラスは静的メンバーのみを含み、インスタンス メンバーを含まないため、拡張できません。 拡張できないため、これは型パラメーターや制約として役に立ちません。静的クラスの特殊化である型は存在できないためです。  
  
## 使用例  
 次の例では CS0717 が生成されます。  
  
```  
// CS0717.cs public static class SC { public static void F() { } } public class G<T> where T : SC  // CS0717 { public static void Main() { } }  
```