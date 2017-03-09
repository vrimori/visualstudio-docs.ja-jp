---
title: "CA1405: COM 参照可能な型の基本型は COM 参照可能でなければなりません | Microsoft Docs"
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
  - "CA1405"
  - "ComVisibleTypeBaseTypesShouldBeComVisible"
helpviewer_keywords: 
  - "CA1405"
  - "ComVisibleTypeBaseTypesShouldBeComVisible"
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1405: COM 参照可能な型の基本型は COM 参照可能でなければなりません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|  
|CheckId|CA1405|  
|分類|Microsoft.Interoperability|  
|互換性に影響する変更点|DependsOnFix|  
  
## 原因  
 コンポーネント オブジェクト モデル \(COM: Component Object Model\) 参照可能な型が、COM 参照不可能な型から派生しています。  
  
## 規則の説明  
 COM 参照可能な型が、新しいバージョンのメンバーを追加するときは、厳密なガイドラインに従い、現在のバージョンにバインドする COM クライアントの動作に悪影響を与えないようにする必要があります。  COM 参照不可能な型が新しいメンバーを追加する場合には、これらの COM バージョン管理規則に従う必要はありません。  ただし、COM 参照可能な型が COM 参照不可能な型から派生し、<xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> または <xref:System.Runtime.InteropServices.ClassInterfaceType> \(既定\) のクラス インターフェイスを公開する場合は、基本型のすべてのメンバー \(COM 参照不可能のマークが付けられているもの以外\) は COM に公開されます。  基本型が新しいメンバーを後続のバージョンに追加した場合、派生型のクラス インターフェイスにバインドされているすべての COM クライアントは適切に動作しなくなります。  COM 参照可能な型は、COM 参照可能な型からのみ派生させる必要があります。これにより、COM クライアントの動作に悪影響を与える可能性を低減できます。  
  
## 違反の修正方法  
 この規則違反を修正するには、基本型を COM 参照可能にするか、派生型を COM 参照不可能にします。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## 使用例  
 この規則に違反する型を次の例に示します。  
  
 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1405-com-visible-type-base-types-should-be-com-visible_1.vb)]
 [!code-cs[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/CSharp/ca1405-com-visible-type-base-types-should-be-com-visible_1.cs)]  
  
## 参照  
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>   
 [Introducing the Class Interface](http://msdn.microsoft.com/ja-jp/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [アンマネージ コードとの相互運用](../Topic/Interoperating%20with%20Unmanaged%20Code.md)