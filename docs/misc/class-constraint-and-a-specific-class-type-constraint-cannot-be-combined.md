---
title: "&#39;Class&#39; 制約と特定のクラス型制約は、組み合わせて使用できません | Microsoft Docs"
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
  - "vbc32107"
  - "bc32107"
helpviewer_keywords: 
  - "BC32107"
ms.assetid: 218a7f0c-dd4f-4086-a52c-e8d581377e8b
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Class&#39; 制約と特定のクラス型制約は、組み合わせて使用できません
制約リストに、[クラス \(Visual Basic\)](http://msdn.microsoft.com/ja-jp/0777c6e6-46bc-451b-ad70-57b49d4ef4f7) 制約と定義済みクラスの名前の両方が含まれています。  
  
 制約リストでは、型パラメーターに渡される型引数の要件が適用されます。 次の要件を任意の組み合わせで指定できます。  
  
-   型引数が 1 つまたは複数のインターフェイスを実装する必要があります  
  
-   型引数は、最大で 1 つのクラスから継承する必要があります  
  
-   型引数は、作成元のコードがアクセスできるパラメーターなしのコンストラクターを公開する必要があります \(`New` 制約を含む\)  
  
 制約リストに特定のクラスまたはインターフェイスを何も含めない場合は、次のいずれかを指定することによって一般的な要件を設定できます。  
  
-   型引数は値型である必要があります \(`Structure` 制約を含む\)  
  
-   型引数は参照型である必要があります \(`Class` 制約を含む\)  
  
 同じ型パラメーターに `Structure` と `Class` の両方を指定することはできません。また、どちらも複数回指定することはできません。  
  
 **エラー ID:** BC32107  
  
### このエラーを解決するには  
  
-   型引数が任意の参照型になることを許可する場合は、制約リストからクラス名を削除します。  
  
-   型引数を特定のクラス名から継承する場合は、制約リストから `Class` キーワードを削除します。  
  
## 参照  
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)