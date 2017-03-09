---
title: "プレフィックスを持つ名前空間宣言は、XML リテラル内に空の値を含むことはできません | Microsoft Docs"
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
  - "bc31184"
  - "vbc31184"
helpviewer_keywords: 
  - "BC31184"
ms.assetid: dde656b4-df3b-4a2e-8871-4e14832ca778
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# プレフィックスを持つ名前空間宣言は、XML リテラル内に空の値を含むことはできません
XML リテラルの XML 名前空間宣言に、名前空間の値が含まれていません。 たとえば、次のコードでは、このエラーが発生します。  
  
```vb#  
Dim book = <book xmlns:ns=""/>  
```  
  
 **エラー ID:** BC31184  
  
### このエラーを解決するには  
  
-   XML 名前空間宣言に有効な名前空間を含めるか、XML リテラルから XML 名前空間宣言を削除します。  
  
     その代わりに、`Imports` ステートメントを使用して、空の名前空間の名前空間プレフィックスを指定することもできます。 例:  
  
    ```vb#  
    Imports <xmlns:ns="">  
    ```  
  
## 参照  
 [XML Literals](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)   
 [Imports Statement \(XML Namespace\)](/dotnet/visual-basic/language-reference/statements/imports-statement-xml-namespace)