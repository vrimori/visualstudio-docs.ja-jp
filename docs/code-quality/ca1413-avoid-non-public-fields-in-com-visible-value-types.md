---
title: "CA1413: Com 参照可能な値型ではパブリックでないフィールドを使用しません | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1413"
  - "AvoidNonpublicFieldsInComVisibleValueTypes"
helpviewer_keywords: 
  - "CA1413"
  - "AvoidNonpublicFieldsInComVisibleValueTypes"
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1413: Com 参照可能な値型ではパブリックでないフィールドを使用しません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|  
|CheckId|CA1413|  
|分類|Microsoft.Interoperability|  
|互換性に影響する変更点|あり|  
  
## 原因  
 コンポーネント オブジェクト モデル \(COM: Component Object Model\) から参照できるというマークが付けられた値型が、非パブリック インスタンス フィールドを宣言しています。  
  
## 規則の説明  
 COM から参照できる値型の非パブリック インスタンス フィールドは、COM クライアントで表示できます。  フィールドの内容を調べて、公開をお勧めできない情報や、設計またはセキュリティに意図しない影響を及ぼす情報が含まれていないかどうかを確認してください。  
  
 既定では、すべてのパブリックな値型を COM から参照できます。  ただし、誤った規則違反のレポートを減らすために、この規則では、COM から参照できる型を明示的に示す必要があります。  包含アセンブリは、<xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> を `false` に設定してマークし、型は、<xref:System.Runtime.InteropServices.ComVisibleAttribute> を `true` に設定してマークする必要があります。  
  
## 違反の修正方法  
 この規則の違反を修正して、フィールドを非表示のままにするには、値型を参照型に変更するか、<xref:System.Runtime.InteropServices.ComVisibleAttribute> 属性を型から削除します。  
  
## 警告を抑制する状況  
 フィールドをパブリックに公開できる場合は、この規則による警告を抑制しても安全です。  
  
## 使用例  
 この規則に違反する型を次の例に示します。  
  
 [!code-cs[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/CSharp/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.cs)]
 [!code-vb[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/VisualBasic/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.vb)]  
  
## 関連規則  
 [CA1407: Com 参照可能な型で静的メンバーを使用しません](../Topic/CA1407:%20Avoid%20static%20members%20in%20COM%20visible%20types.md)  
  
 [CA1017: アセンブリに ComVisibleAttribute を設定します](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## 参照  
 [アンマネージ コードとの相互運用](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [相互運用のための .NET 型の要件](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)