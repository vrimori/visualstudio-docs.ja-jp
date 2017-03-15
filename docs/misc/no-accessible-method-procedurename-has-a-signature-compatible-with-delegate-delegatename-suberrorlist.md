---
title: "デリゲート &#39;&lt;delegatename&gt;&#39;:&lt;suberrorlist&gt; と互換性のあるシグネチャを持つアクセス可能なメソッド &#39;&lt;procedurename&gt;&#39; がありません | Microsoft Docs"
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
  - "bc30950"
  - "vbc30950"
helpviewer_keywords: 
  - "BC30950"
ms.assetid: c1938099-2c03-491e-b599-d0c43bf94baf
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# デリゲート &#39;&lt;delegatename&gt;&#39;:&lt;suberrorlist&gt; と互換性のあるシグネチャを持つアクセス可能なメソッド &#39;&lt;procedurename&gt;&#39; がありません
代入ステートメントによってプロシージャのアドレスがデリゲート変数に代入されましたが、シグネチャが一致するプロシージャのバージョンをコンパイラが見つけられません。  
  
 コードがプロシージャのアドレスを使用する場合、デリゲートとパラメーター リストが一致するプロシージャのバージョンをコンパイラは見つけようとします。 プロシージャがオーバーロードされたいくつかのバージョンで定義されている場合、コンパイラはシグネチャが一致する単一のバージョンを見つけようとします。 詳細については、「[Overload Resolution](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution)」を参照してください。  
  
 コンパイラは、シグネチャが一致するプロシージャのバージョンを見つけられない場合に、このエラーを生成します。 たとえば、プロシージャまたはデリゲートがジェネリックで、これに型引数が渡され、他のシグネチャと一致しないシグネチャが提供される場合に発生します。  
  
 **エラー ID:** BC30950  
  
### このエラーを解決するには  
  
1.  プロシージャまたはデリゲートを再定義し、パラメーター リストが一致するようにします。  
  
     または  
  
     プロシージャとパラメーター リストが一致する新しいデリゲートを定義するか、デリゲートとパラメーター リストが一致する新しいプロシージャを定義します。  
  
2.  プロシージャまたはデリゲートがジェネリックの場合は、シグネチャが他のシグネチャと一致する型引数を渡します。  
  
## 参照  
 [AddressOf Operator](/dotnet/visual-basic/language-reference/operators/addressof-operator)   
 [Delegate Statement](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [ビルド内にありません: デリゲートと AddressOf 演算子](http://msdn.microsoft.com/ja-jp/7b2ed932-8598-4355-b2f7-5cedb23ee86f)   
 [Overload Resolution](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution)   
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)