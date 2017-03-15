---
title: "コンパイラの警告 (レベル 2) CS0114 | Microsoft Docs"
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
  - "CS0114"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0114"
ms.assetid: 9647772b-d581-4620-981e-f9c607d4a1af
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 2) CS0114
'function1' は継承されたメンバー 'function2' を非表示にします。 現在のメソッドでその実装をオーバーライドするには、override キーワードを追加します。 オーバーライドしない場合は、new キーワードを追加します。  
  
 クラス内の宣言が、基底クラス内の宣言と競合しています。このため、基底クラスのメンバーは非表示になります。  
  
 詳細については、「[base](/dotnet/csharp/language-reference/keywords/base)」を参照してください。  
  
 次の例では CS0114 が生成されます。  
  
```  
// CS0114.cs // compile with: /W:2 /warnaserror abstract public class clx { public abstract void f(); } public class cly : clx { public void f() // CS0114, hides base class member // try the following line instead // override public void f() { } public static void Main() { } }  
```