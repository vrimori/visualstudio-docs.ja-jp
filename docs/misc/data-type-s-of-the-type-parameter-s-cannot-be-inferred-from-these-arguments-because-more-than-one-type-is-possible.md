---
title: "型パラメーターのデータ型は複数になる可能性があるため、これらの引数から推定することはできません | Microsoft Docs"
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
  - "vbc36653"
  - "bc36653"
  - "vbc36650"
  - "bc36650"
helpviewer_keywords: 
  - "BC36650"
  - "BC36653"
ms.assetid: 79287e1f-7070-4a71-96d2-aee0a0c9d8bd
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 型パラメーターのデータ型は複数になる可能性があるため、これらの引数から推定することはできません
型パラメーターのデータ型は複数になる可能性があるため、これらの引数から推論することはできません。 データ型を明示的に指定すると、このエラーを修正できる場合があります。  
  
 このエラーは、オーバーロードの解決法が失敗したときに発生します。 これは、特定のオーバーロード候補が削除された理由を示す従属メッセージとして発生します。 このエラーは、呼び出されるジェネリック プロシージャの型パラメーターのデータ型を決定するために型の推定が適用されている場合は、コンパイラが少なくとも型パラメーターの 1 つに対して複数のデータ型を検出することを示します。  
  
> [!NOTE]
>  引数を指定できない \(たとえば、クエリ式のクエリ演算子\) 場合は、このエラー メッセージが 2 番目の文なしで表示されます。  
  
 使用例を含む詳細については、「[メソッド '\<methodname\>' 内の型パラメーターのデータ型は複数になる可能性があるため、これらの引数から推論することはできません](../Topic/Data%20type\(s\)%20of%20the%20type%20parameter\(s\)%20in%20method%20'%3Cmethodname%3E'%20cannot%20be%20inferred%20from%20these%20arguments%20because%20more%20than%20one%20type%20is%20possible.md)」を参照してください。  
  
 **エラー ID:** BC36653 および BC36650  
  
## 参照  
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Overload Resolution](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution)