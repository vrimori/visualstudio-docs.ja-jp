---
title: "型 &#39;&lt;type1&gt;&#39; の値を &#39;&lt;type2&gt;&#39; に変換できません | Microsoft Docs"
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
  - "bc30311"
  - "vbc30311"
helpviewer_keywords: 
  - "BC30311"
ms.assetid: e3a513d4-2a1e-46d6-b592-b2e756b89d7d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 型 &#39;&lt;type1&gt;&#39; の値を &#39;&lt;type2&gt;&#39; に変換できません
ステートメントは、定義されていない方法で、あるデータ型を別のデータ型に変換しようとしています。 このエラーの原因として以下が考えられます。  
  
-   変換で指定されている 2 つのデータ型の間に変換が存在しない。 この種の変換例としては、`Boolean` 値から `Date` 型への変換があります。  
  
-   配列の初期化で、`New` 句の後に中かっこ \(`{}`\) がない。 この場合は、\<type2\> の形式は '\<type\> の 1 次元配列' です。  
  
 **エラー ID:** BC30311  
  
### このエラーを解決するには  
  
-   式がターゲットのデータ型に変換できることをご確認ください。  
  
-   \<type2\> が配列の場合は、`New` 句で、型名の後にかっこと中かっこの両方が含まれていることを確かめてください。 次のコードは、配列の適切な初期化を示しています。  
  
    ```  
    Dim anIntArray As Integer() = New Integer() {}  
    ```  
  
## 参照  
 [Type Conversions in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)   
 [How to: Initialize an Array Variable in Visual Basic](../Topic/How%20to:%20Initialize%20an%20Array%20Variable%20in%20Visual%20Basic.md)