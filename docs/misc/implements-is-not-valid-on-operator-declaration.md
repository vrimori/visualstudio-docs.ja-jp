---
title: "&#39;Implements&#39; は演算子の宣言で有効ではありません | Microsoft Docs"
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
  - "vbc33004"
  - "bc33004"
helpviewer_keywords: 
  - "BC33004"
ms.assetid: 22f27f4d-4bbd-4f8f-a6e8-0fc10efb268d
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Implements&#39; は演算子の宣言で有効ではありません
[Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement) に [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause) キーワードが指定されています。  
  
 `Function` または `Sub` プロシージャ、プロパティ、あるいはイベントのみが、インターフェイスのメンバーを実装できます。 実装の詳細については、「[ビルド内にありません: Visual Basic でのインターフェイスの実装例](http://msdn.microsoft.com/ja-jp/50bf2a30-73b6-4126-a921-075fd6eec278)」を参照してください。  
  
 `Operator` プロシージャには `Public` キーワードと `Shared` キーワードの両方が必要です。変換演算子には `Widening` キーワードか `Narrowing` キーワードのいずれかが必要です。 詳細については、「[Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)」を参照してください。  
  
 **エラー ID:** BC33004  
  
### このエラーを解決するには  
  
-   インターフェイスのメンバーを実装するためにこの手順を実行する場合、`Function` または `Sub` プロシージャ、プロパティ、あるいはイベントとして修正します。  
  
-   演算子を定義するためにこの手順を使用する場合、その宣言から `Implements` キーワードを削除します。  
  
## 参照  
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)