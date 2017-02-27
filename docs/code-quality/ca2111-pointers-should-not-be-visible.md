---
title: "CA2111: ポインターは参照可能にすることはできません | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PointersShouldNotBeVisible"
  - "CA2111"
helpviewer_keywords: 
  - "CA2111"
  - "PointersShouldNotBeVisible"
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA2111: ポインターは参照可能にすることはできません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PointersShouldNotBeVisible|  
|CheckId|CA2111|  
|分類|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## 原因  
 パブリックまたはプロテクトの <xref:System.IntPtr?displayProperty=fullName> フィールドまたは <xref:System.UIntPtr?displayProperty=fullName> フィールドが読み取り専用ではありません。  
  
## 規則の説明  
 <xref:System.IntPtr> と <xref:System.UIntPtr> は、アンマネージ メモリにアクセスするときに使用するポインターの型です。  ポインターがプライベート、内部、または読み取り専用のいずれでもない場合、悪意のあるコードで、ポインターの値が変更される可能性があります。結果的に、メモリの任意の位置にアクセスされたり、アプリケーション エラーやシステム エラーの原因になります。  
  
 ポインターのフィールドを含む型に対するアクセスを保護するには、「[CA2112: セキュリティで保護された型はフィールドを公開してはなりません](../code-quality/ca2112-secured-types-should-not-expose-fields.md)」を参照してください。  
  
## 違反の修正方法  
 読み取り専用、内部、またはプライベートにすることで、ポインターを保護します。  
  
## 警告を抑制する状況  
 ポインターの値に依存していない場合は、この規則による警告を抑制します。  
  
## 使用例  
 この規則に違反するポインターと適合するポインターを次のコードに示します。  ポインターをプライベートにしないと、規則「[CA1051: 参照できるインスタンス フィールドを宣言しないでください](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)」にも違反するので注意してください。  
  
 [!code-cs[FxCop.Security.PointersArePrivate#1](../code-quality/codesnippet/CSharp/ca2111-pointers-should-not-be-visible_1.cs)]  
  
## 関連規則  
 [CA2112: セキュリティで保護された型はフィールドを公開してはなりません](../code-quality/ca2112-secured-types-should-not-expose-fields.md)  
  
 [CA1051: 参照できるインスタンス フィールドを宣言しないでください](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)  
  
## 参照  
 <xref:System.IntPtr?displayProperty=fullName>   
 <xref:System.UIntPtr?displayProperty=fullName>