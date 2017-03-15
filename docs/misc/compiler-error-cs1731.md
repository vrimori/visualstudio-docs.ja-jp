---
title: "コンパイラ エラー CS1731 | Microsoft Docs"
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
  - "CS1731"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1731"
ms.assetid: 267b32aa-a692-4a54-8654-0540ee36c0a0
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1731
デリゲート戻り値の型に暗黙的に変換できない戻り値の型がブロック内にあるため、'expression' をデリゲートに変換することはできません。  
  
 このエラーは、ラムダ式または匿名メソッドに、デリゲートの戻り値の型と互換性がない戻り値の型がある場合に生成されます。  
  
### このエラーを解決するには  
  
1.  デリゲートまたは式の戻り値の型を変更します。  
  
## 使用例  
 次のコードでは CS1731 が生成されます。  
  
```  
class CS1731 { delegate double D(); D d = () => { return "Who knows the real sword of Gryffindor?"; }; }  
```