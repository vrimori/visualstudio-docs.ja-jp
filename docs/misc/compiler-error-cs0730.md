---
title: "コンパイラ エラー CS0730 | Microsoft Docs"
ms.custom: ""
ms.date: "09/30/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0730"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0730"
ms.assetid: bf291285-dc1e-4c8d-a449-119004adc088
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0730
型 'type' は、'type' の入れ子にされた型なので、転送できません。  
  
 入れ子になったクラスを転送しようとすると、このエラーが生成されます。  
  
## 使用例  
 次の例では CS0730 が生成されます。 これは、2 つのソース ファイルで構成されます。 最初にライブラリ ファイル `CS0730a.cs` をコンパイルし、次にそのライブラリ ファイルを参照しているファイル `CS0730.cs` をコンパイルします。  
  
```  
// CS0730a.cs // compile with: /t:library public class Outer { public class Nested {} }  
```  
  
```  
// CS0730.cs // compile with: /t:library /r:CS0730a.dll using System.Runtime.CompilerServices; [assembly:TypeForwardedToAttribute(typeof(Outer.Nested))]   // CS0730 [assembly:TypeForwardedToAttribute(typeof(Outer))]   // OK  
```