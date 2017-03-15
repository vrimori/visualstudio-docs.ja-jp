---
title: "コンパイラ エラー CS0533 | Microsoft Docs"
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
  - "CS0533"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0533"
ms.assetid: f8b38c5a-d365-4081-a101-6282bdd19069
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0533
'derived\-class member' は継承された抽象メンバー 'base\-class member' を非表示にします  
  
 基底[クラス](/dotnet/csharp/language-reference/keywords/class) メソッドは非表示になります。 宣言の構文が正しいかどうかを確認します。  
  
 詳細については、「[base](/dotnet/csharp/language-reference/keywords/base)」を参照してください。  
  
 次の例では CS0533 が生成されます。  
  
```  
// CS0533.cs namespace x { abstract public class a { abstract public void f(); } abstract public class b : a { new abstract public void f();   // CS0533 // try the following lines instead // override public void f() // { // } public static void Main() { } } }  
```