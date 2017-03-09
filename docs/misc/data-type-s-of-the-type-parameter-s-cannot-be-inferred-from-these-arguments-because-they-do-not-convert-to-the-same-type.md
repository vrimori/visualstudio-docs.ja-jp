---
title: "型パラメーターの 1 つ以上のデータ型は同じ型には変換されないため、これらの引数から推論することはできません。 | Microsoft Docs"
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
  - "vbc36659"
  - "bc36659"
  - "vbc36656"
  - "bc36656"
helpviewer_keywords: 
  - "BC36659"
  - "BC36656"
ms.assetid: 0aa809da-3b44-4d78-b3c5-0a148bdf7ce8
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 型パラメーターの 1 つ以上のデータ型は同じ型には変換されないため、これらの引数から推論することはできません。
型パラメーターの 1 つ以上のデータ型は同じ型には変換されないため、これらの引数から推論することはできません。 データ型を明示的に指定すると、このエラーを修正できる場合があります。  
  
 このエラーは、オーバーロードの解決法が失敗したときに発生します。 これは、特定のオーバーロード候補が削除された理由を示す従属メッセージとして発生します。 エラーは、コンパイラが型の推定を使用して、引数と互換性のある型パラメーターのデータ型を検索することができないことを説明します。  
  
> [!NOTE]
>  引数を指定できない \(たとえば、クエリ式のクエリ演算子\) 場合は、このエラー メッセージが 2 番目の文なしで表示されます。  
  
 使用例を含む詳細については、「[メソッド '\<methodname\>' 内の型パラメーターの 1 つ以上のデータ型が同じ型には変換されないため、これらの引数から推論することはできません](../Topic/Data%20type\(s\)%20of%20the%20type%20parameter\(s\)%20in%20method%20'%3Cmethodname%3E'%20cannot%20be%20inferred%20from%20these%20arguments%20because%20they%20do%20not%20convert%20to%20the%20same%20type.md)」を参照してください。  
  
 **エラー ID:** BC36659 および BC36656  
  
## 参照  
 [Relaxed Delegate Conversion](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Overload Resolution](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution)