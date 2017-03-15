---
title: "コンパイラ エラー CS1041 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1041"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1041"
ms.assetid: 9f62c058-cd28-4cb5-835c-d0f25f4fd08e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1041
識別子が必要です。'keyword' はキーワードです  
  
 識別子を指定する必要がある場所で C\# 言語の予約語が見つかりました。[keyword](/dotnet/csharp/language-reference/keywords/index) をユーザー指定の識別子で置き換えます。  
  
## 使用例  
 次の例では CS1041 が生成されます。  
  
```  
// CS1041a.cs class MyClass { public void f(int long)   // CS1041 // Try the following instead: // public void f(int i) { } public static void Main() { } }  
```  
  
## 使用例  
 予約語の同じセットがない別のプログラミング言語からインポートする場合は、次の例に示すように、予約されている識別子を @ プレフィックスで変更できます。  
  
 `@` プレフィックスを持つ識別子は、逐語的識別子と呼ばれます。  
  
```  
// CS1041b.cs class MyClass { public void f(int long)   // CS1041 // Try the following instead: // public void f(int @long) { } public static void Main() { } }  
```