---
title: "演算子 &#39;&lt;operatorsymbol&gt;&#39; が、すべてのコード パスで値を返しません | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42106"
  - "bc42106"
helpviewer_keywords: 
  - "BC42106"
ms.assetid: 175b2bc9-5233-462d-97de-9d97b003cc46
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 演算子 &#39;&lt;operatorsymbol&gt;&#39; が、すべてのコード パスで値を返しません
演算子 '\<operatorsymbol\>' が、すべてのコード パスで値を返しません。 この結果が使用されると、実行時に Null 参照例外が生じる可能性があります。  
  
 演算子プロシージャには、値を返さないコードのパスが少なくとも 1 つ含まれています。  
  
 演算子プロシージャから値を返すには、これを [Return Statement](/dotnet/visual-basic/language-reference/statements/return-statement) に含めるしかありません。  
  
 制御が `End Operator` ステートメントに渡されると、演算子プロシージャは、プロパティのデータ型の既定値を返します。 詳しくは、「[Function Statement](/dotnet/visual-basic/language-reference/statements/function-statement)」の「動作」をご覧ください。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法について詳しくは、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」をご覧ください。  
  
 **エラー ID:** BC42106  
  
### このエラーを解決するには  
  
-   制御フロー ロジックを確認し、可能性のあるすべてのパスが `Return` ステートメントで終わっていることを確かめてください。 特に、`End Operator` の前の最後のステートメントは、`Return` ステートメントでなければなりません。  
  
## 参照  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)