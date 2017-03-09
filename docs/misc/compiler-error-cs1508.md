---
title: "コンパイラ エラー CS1508 | Microsoft Docs"
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
  - "CS1508"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1508"
ms.assetid: 979bc615-58ce-49f8-ba73-e6cf57c56418
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1508
リソース識別子 'identifier' はアセンブリで既に使用されています  
  
 コンパイルで、同じ識別子 \(***identifier***\) が、2 つ以上の [\/resource](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option) または [\/linkresource](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option) コンパイラ オプションに渡されました。  
  
 たとえば、次のオプションでは CS1508 が生成されます。  
  
```  
/resource:anyfile.bmp,DuplicatIdent /linkresource:a.bmp,DuplicatIdent  
```