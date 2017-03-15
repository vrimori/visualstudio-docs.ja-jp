---
title: "CA1406: Visual Basic 6 クライアントに対しては Int64 引数を使用しません | Microsoft Docs"
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
  - "AvoidInt64ArgumentsForVB6Clients"
  - "CA1406"
helpviewer_keywords: 
  - "AvoidInt64ArgumentsForVB6Clients"
  - "CA1406"
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1406: Visual Basic 6 クライアントに対しては Int64 引数を使用しません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidInt64ArgumentsForVB6Clients|  
|CheckId|CA1406|  
|分類|Microsoft.Interoperability|  
|互換性に影響する変更点|あり|  
  
## 原因  
 コンポーネント オブジェクト モデル \(COM: Component Object Model\) から参照可能として個別にマークされた型が、<xref:System.Int64?displayProperty=fullName> 引数を受け取るメンバーを宣言しています。  
  
## 規則の説明  
 Visual Basic 6 COM クライアントでは、64 ビット整数にアクセスできません。  
  
 既定で COM から参照できるものは、アセンブリ、パブリック型、パブリック型のパブリック インスタンス メンバー、パブリック値型のすべてのメンバーです。  ただし、誤った規則違反のレポートを減らすために、この規則では、COM から参照できる型を明示的に示す必要があります。包含アセンブリは、<xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> を `false` に設定してマークし、型は、<xref:System.Runtime.InteropServices.ComVisibleAttribute> を `true` に設定してマークする必要があります。  
  
## 違反の修正方法  
 値を常に 32 ビット整数で表せるパラメーターについて、この規則違反を修正するには、パラメーター型を <xref:System.Int32?displayProperty=fullName> に変更します。  パラメーターの値が 32 ビット整数で表すことができる値を超える可能性がある場合は、パラメーター型を <xref:System.Decimal?displayProperty=fullName> に変更します。  <xref:System.Single?displayProperty=fullName> と <xref:System.Double?displayProperty=fullName> のどちらでも、<xref:System.Int64> データ型の上限で有効桁数が失われることに注意してください。  メンバーが COM から参照できないようにするには、<xref:System.Runtime.InteropServices.ComVisibleAttribute> を `false` に設定してください。  
  
## 警告を抑制する状況  
 Visual Basic 6 COM クライアントでその型にアクセスしないことが明確な場合には、この規則による警告を抑制しても安全です。  
  
## 使用例  
 この規則に違反する型を次の例に示します。  
  
 [!code-cs[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/CSharp/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.cs)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/VisualBasic/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.vb)]  
  
## 関連規則  
 [CA1413: Com 参照可能な値型ではパブリックでないフィールドを使用しません](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
 [CA1407: Com 参照可能な型で静的メンバーを使用しません](../Topic/CA1407:%20Avoid%20static%20members%20in%20COM%20visible%20types.md)  
  
 [CA1017: アセンブリに ComVisibleAttribute を設定します](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## 参照  
 [アンマネージ コードとの相互運用](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Long Data Type](/dotnet/visual-basic/language-reference/data-types/long-data-type)