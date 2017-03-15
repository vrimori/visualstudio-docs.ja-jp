---
title: "&#39;System.Runtime.InteropServices.DllImportAttribute&#39; は、ジェネリック、またはジェネリック型の入れ子になっているメソッドには適用できません。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31526"
  - "bc31526"
helpviewer_keywords: 
  - "BC31526"
ms.assetid: 6f153808-1945-4c99-85ae-8bd3b35ee5a2
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System.Runtime.InteropServices.DllImportAttribute&#39; は、ジェネリック、またはジェネリック型の入れ子になっているメソッドには適用できません。
プロシージャが <xref:System.Runtime.InteropServices.DllImportAttribute> で宣言されていますが、プロシージャがジェネリックか、ジェネリック クラスまたは構造体に含まれています。  
  
 共通言語ランタイム \(CLR\) は、.NET Framework 外のアンマネージ DLL \(Dynamic\-Link Library\) の中で定義されている置換プロシージャを指定しているときに、この属性と <xref:System.Runtime.InteropServices._Assembly.EntryPoint%2A> プロパティを認識します。<xref:System.Runtime.InteropServices.DllImportAttribute> が適用されているプロシージャがコードから呼び出されると、共通言語ランタイムは、そのプロシージャの代わりに指定されたアンマネージ プロシージャを呼び出します。  
  
 .NET Framework 外のアンマネージ プラットフォームはジェネリック型を認識しないため、ジェネリック型を使用してそれらのプラットフォームとの相互運用を可能にすることはできません。  
  
 **エラー ID:** BC31526  
  
### このエラーを解決するには  
  
-   プロシージャもそのコンテナーもジェネリックである必要がない場合は、ジェネリックにならないように `Of` 句を削除します。  
  
-   プロシージャまたはそのコンテナーがジェネリックである必要がある場合は、このプロシージャの宣言から <xref:System.Runtime.InteropServices.DllImportAttribute> を削除します。  
  
## 参照  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)