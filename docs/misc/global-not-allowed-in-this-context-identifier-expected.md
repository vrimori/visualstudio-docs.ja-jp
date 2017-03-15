---
title: "&#39;Global&#39; はこのコンテキストで許可されていません。識別子を指定してください | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36001"
  - "bc36001"
helpviewer_keywords: 
  - "BC36001"
ms.assetid: d515daa2-f53d-424c-81fd-e9c4b12f331b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Global&#39; はこのコンテキストで許可されていません。識別子を指定してください
`Global` キーワードを許可されていないステートメントで使用しています。  
  
 `Global` キーワードを使用すると、コードがコンパイルされる名前空間階層の外部に定義された名前空間にアクセスできます。`Global` は、.NET Framework クラス ライブラリの最も外側の名前空間レベルで修飾パスを開始します。 例については、「[Global \- delete](http://msdn.microsoft.com/ja-jp/18c8ba14-40f6-4978-8096-6a5852324635)」を参照してください。  
  
 ステートメントの中には、`Imports` や `Namespace` のように、コードがコンパイルされる名前空間から独立しているものもあります。 これらのステートメントでは、<xref:System> や <xref:Microsoft.VisualBasic> のように、ルート レベルの名前空間から始まる完全修飾パスが必要です。 このようなステートメントで、`Global` キーワードは不要であり、許可されていません。  
  
 **エラー ID:** BC36001  
  
### このエラーを解決するには  
  
-   ステートメントから `Global` キーワードを削除します。 これは必要ありません。  
  
## 参照  
 [Global \- delete](http://msdn.microsoft.com/ja-jp/18c8ba14-40f6-4978-8096-6a5852324635)   
 [Imports Statement \(.NET Namespace and Type\)](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type)   
 [Namespace Statement](/dotnet/visual-basic/language-reference/statements/namespace-statement)   
 [References and the Imports Statement](/dotnet/visual-basic/programming-guide/program-structure/references-and-the-imports-statement)