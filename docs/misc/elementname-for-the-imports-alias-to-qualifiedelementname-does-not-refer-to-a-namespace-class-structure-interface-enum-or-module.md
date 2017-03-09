---
title: "&#39;&lt;qualifiedelementname&gt;&#39; への Imports エイリアス &#39;&lt;elementname&gt;&#39; は、Namespace、Class、Structure、Interface、Enum または Module を参照していません | Microsoft Docs"
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
  - "bc30798"
  - "vbc30798"
helpviewer_keywords: 
  - "BC30798"
ms.assetid: bfa66627-516a-4955-977d-92372bcea090
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;qualifiedelementname&gt;&#39; への Imports エイリアス &#39;&lt;elementname&gt;&#39; は、Namespace、Class、Structure、Interface、Enum または Module を参照していません
[Imports Statement \(.NET Namespace and Type\)](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type) で、インポートできないプログラミング要素が指定されています。  
  
 `Imports` ステートメントは、要素名の前に修飾文字列を使用する必要性を減らすか無くすために使用します。 要素の一意な宣言への明確なパスを指定するために、`Imports` ステートメント自体の中で要素を修飾します。 その後は、要素への参照を修飾する必要はありません。  
  
 `Imports` は名前空間で最もよく使用されますが、クラス、モジュール、構造体、インターフェイス、または列挙型をインポートして、長い修飾文字列を使用せずにその要素を参照することもできます。  
  
 詳細については、[「ビルド内にありません: 同じ名前を持つ複数の変数がある場合に参照を解決する」](http://msdn.microsoft.com/ja-jp/9601e39f-1911-44e1-ace5-3f6e090408b9)の「コンテナー要素のインポート」をご覧ください。  
  
 **エラー ID:** BC30798  
  
### このエラーを解決するには  
  
1.  `Imports` ステートメントの修飾文字列内の要素のスペルを確認します。特に、文字列の最後にある修飾対象の要素を確認します。  
  
2.  修飾対象の要素の型が正しい \(名前空間、クラス、モジュール、構造体、インターフェイス、または列挙型\) ことを確認します。 正しくない場合は、`Imports` ステートメントを削除します。  
  
## 参照  
 [References and the Imports Statement](/dotnet/visual-basic/programming-guide/program-structure/references-and-the-imports-statement)