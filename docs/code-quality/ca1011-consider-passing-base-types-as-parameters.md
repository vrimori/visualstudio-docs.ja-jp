---
title: "CA1011: 基本型をパラメーターとして渡すことを考慮します | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ConsiderPassingBaseTypesAsParameters"
  - "CA1011"
helpviewer_keywords: 
  - "CA1011"
  - "ConsiderPassingBaseTypesAsParameters"
ms.assetid: ce1e1241-dcf4-419b-9363-1d5bc4989279
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1011: 基本型をパラメーターとして渡すことを考慮します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ConsiderPassingBaseTypesAsParameters|  
|CheckId|CA1011|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## 原因  
 メソッドの宣言に派生型の仮パラメーターが含まれ、そのメソッドはパラメーターの基本型のメンバーのみを呼び出しています。  
  
## 規則の説明  
 メソッドの宣言で基本型をパラメーターとして指定すると、その基本型から派生した型は、メソッドに対応する引数として渡すことができます。  メソッドの本体内で引数を使用すると、実行される固有のメソッドは、その引数の型によって変わります。  派生型で実現する追加機能が不要である場合、基本型を使用することでメソッドをより広範囲に利用できるようになります。  
  
## 違反の修正方法  
 この規則違反を修正するには、パラメーターの型を基本型に変更します。  
  
## 警告を抑制する状況  
 次の場合は、この規則による警告を抑制しても安全です。  
  
-   派生型によって実現する固有の機能がメソッドに必要である場合  
  
     または  
  
-   その派生型 \(またはより強い派生型\) しかメソッドに渡せないようにする場合  
  
 この場合、コンパイラやランタイムで厳密な型チェックが実行されるため、コードの信頼性が高くなります。  
  
## 使用例  
 <xref:System.IO.FileStream> オブジェクトのみと使用できるメソッド `ManipulateFileStream` を次の例に示します。これは規則違反です。  2 つ目のメソッド `ManipulateAnyStream` は、<xref:System.IO.FileStream> パラメーターを <xref:System.IO.Stream> で置換することで規則に適合しています。  
  
 [!code-cs[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CSharp/ca1011-consider-passing-base-types-as-parameters_1.cs)]
 [!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CPP/ca1011-consider-passing-base-types-as-parameters_1.cpp)]
 [!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1011-consider-passing-base-types-as-parameters_1.vb)]  
  
## 関連規則  
 [CA1059: メンバーは特定の具象型を公開できません](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)