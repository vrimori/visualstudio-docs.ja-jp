---
title: "コンパイラ エラー CS0509 | Microsoft Docs"
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
  - "CS0509"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0509"
ms.assetid: dc113e03-7a01-489b-b886-51ee056fc96a
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0509
'class1': シール型 'class2' から派生することはできません  
  
 [シール](/dotnet/csharp/language-reference/keywords/sealed) クラスは[基底](/dotnet/csharp/language-reference/keywords/base)クラスとしては機能しません。 既定では、構造体はシールされています。  
  
 次の例では CS0509 が生成されます。  
  
```  
// CS0509.cs // compile with: /target:library sealed public class clx {} public class cly : clx {}   // CS0509  
```