---
title: "コンパイラ エラー CS0061 | Microsoft Docs"
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
  - "CS0061"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0061"
ms.assetid: 8dfc57a9-653d-4902-a88c-92032ba64024
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0061
アクセシビリティに一貫性がありません。基本インターフェイス 'interface 1' のアクセシビリティはインターフェイス 'interface 2' よりも低く設定されています  
  
 [パブリック](/dotnet/csharp/language-reference/keywords/public) コンストラクトは、パブリックにアクセスできるオブジェクトを返す必要があります。  
  
 インターフェイスのアクセシビリティを、派生インターフェイスで制限することはできません。 詳細については、次のトピックを参照してください。[インターフェイス](/dotnet/csharp/programming-guide/interfaces/index) および[アクセス修飾子](/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers).  
  
 次の例では CS0061 が生成されます。  
  
```  
// CS0061.cs // compile with: /target:library internal interface A {} public interface AA : A {}  // CS0061 // OK public interface B {} internal interface BB : B {} internal interface C {} internal interface CC : C {}  
```