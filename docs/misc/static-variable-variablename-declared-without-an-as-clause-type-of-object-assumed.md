---
title: "静的変数 &#39;&lt;variablename&gt;&#39; の宣言に &#39;As&#39; 句がありません。&#39;Object&#39; の型と見なされます | Microsoft Docs"
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
  - "vbc42111"
  - "bc42111"
helpviewer_keywords: 
  - "BC42111"
ms.assetid: ca6b625c-21a5-45f7-ac67-282f6993a724
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 静的変数 &#39;&lt;variablename&gt;&#39; の宣言に &#39;As&#39; 句がありません。&#39;Object&#39; の型と見なされます
コンパイラは、静的ローカル変数のデータ型を推論しません。 次の例では、`Option Strict` が `Off` に設定されており、`m` の型は、`Option Infer` が `On` に設定されているか `Off` に設定されているかに関係なく、`Object` になります。 ローカル型推論は適用されません。  
  
```  
Sub Main() Static m = 10 End Sub  
```  
  
 既定では、このメッセージは警告です。 警告を表示しない方法や、警告をエラーとして扱う方法については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」を参照してください。  
  
 **エラー ID:** BC42111  
  
### この警告に対処するには  
  
-   静的ローカル変数のデータ型を指定します。  
  
     たとえば、前の例の `m` を `Integer` 型にする場合は、宣言で型を指定します。  
  
    ```  
    Sub Main() Static m As Integer = 10 End Sub  
  
    ```  
  
## 参照  
 [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [ビルド内にありません: 方法: 変数の有効期間を延長する](http://msdn.microsoft.com/ja-jp/04e7c56c-1db0-4fe5-a678-859a39ec654b)   
 [Local Type Inference](/dotnet/visual-basic/programming-guide/language-features/variables/local-type-inference)   
 [Option Infer Statement](/dotnet/visual-basic/language-reference/statements/option-infer-statement)   
 [Static](/dotnet/visual-basic/language-reference/modifiers/static)