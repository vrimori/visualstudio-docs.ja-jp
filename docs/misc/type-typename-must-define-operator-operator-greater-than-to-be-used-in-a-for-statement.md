---
title: "型 &#39;&lt;typename&gt;&#39; を &#39;For&#39; ステートメントで使用するには、演算子 &#39;&lt;operator&gt;&#39; を定義しなければなりません | Microsoft Docs"
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
  - "vbc33038"
  - "BC33038"
helpviewer_keywords: 
  - "BC33038"
ms.assetid: b1c9d87f-80f9-4c8c-8908-f8400b9fe4c5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 型 &#39;&lt;typename&gt;&#39; を &#39;For&#39; ステートメントで使用するには、演算子 &#39;&lt;operator&gt;&#39; を定義しなければなりません
`For` ループが、必要な演算子をサポートしていない型のカウンター変数を指定しています。  
  
 `For` ループ内のカウンター変数は、次の演算子のすべてをサポートする任意のデータ型にすることができます。  
  
-   以上 \(`>=`\)  
  
-   以下 \(`<=`\)  
  
-   加算 \(`+`\)  
  
-   減算 \(`-`\)  
  
 カウンター変数に数値データ型を使用する場合、先行するすべての演算子がサポートされます。 ユーザー定義のクラスまたは構造体を使用する場合、そのクラスまたは構造体の先行するすべての演算子を定義する必要があります。  
  
 `For` ステートメント内の `start`、`end`、および `step` 式のデータ型はカウンター変数のデータ型に拡大変換する必要があることにも注意してください。 カウンター変数がユーザー定義のクラスまたは構造体で、`start`、`end`、または `step` 式が異なる型である場合、`CType` 変換演算子を定義して、必要な変換を実現する必要があります。  
  
 **エラー ID:** BC33038  
  
### このエラーを解決するには  
  
1.  カウンター変数のデータ型のスペルが正しいことを確認します。  
  
2.  ユーザー定義のクラスまたは構造体をカウンター変数に使用する場合は、そのクラスまたは構造体に必要なすべての演算子を定義します。  
  
3.  `start`、`end`、および `step` 式のデータ型によっては、それらをカウンター変数のデータ型に変換するための 1 つ以上の `CType` 変換演算子を定義する必要がある場合があります。  
  
## 参照  
 [For...Next ステートメント](/dotnet/visual-basic/language-reference/statements/for-next-statement)   
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [CType 関数](/dotnet/visual-basic/language-reference/functions/ctype-function)