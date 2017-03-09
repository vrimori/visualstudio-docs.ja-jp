---
title: "CA1409: COM 参照可能な型は作成可能でなければなりません | Microsoft Docs"
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
  - "ComVisibleTypesShouldBeCreatable"
  - "CA1409"
helpviewer_keywords: 
  - "ComVisibleTypesShouldBeCreatable"
  - "CA1409"
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1409: COM 参照可能な型は作成可能でなければなりません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ComVisibleTypesShouldBeCreatable|  
|CheckId|CA1409|  
|分類|Microsoft.Interoperability|  
|互換性に影響する変更点|なし|  
  
## 原因  
 コンポーネント オブジェクト モデル \(COM: Component Object Model\) から参照できると明確にマークされている参照型に、パブリックのパラメーター付きコンストラクターが含まれますが、パブリックの既定 \(パラメーターなし\) コンストラクターが含まれません。  
  
## 規則の説明  
 パブリックの既定コンストラクターがない型は、COM クライアントで作成できません。  ただし、別の手段で型を作成してクライアントに渡すことができる場合 \(メソッド呼び出しの戻り値を使用するなど\)、COM クライアントからその型にアクセスできます。  
  
 この規則では、<xref:System.Delegate?displayProperty=fullName> から派生した型は無視されます。  
  
 既定で COM から参照できるものは、アセンブリ、パブリック型、パブリック型のパブリック インスタンス メンバー、パブリック値型のすべてのメンバーです。  
  
## 違反の修正方法  
 この規則違反を修正するには、パブリックの既定コンストラクターを追加するか、型から <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> を削除します。  
  
## 警告を抑制する状況  
 オブジェクトを作成して COM クライアントに渡すための別の方法がある場合は、この規則による警告を抑制しても安全です。  
  
## 関連規則  
 [CA1017: アセンブリに ComVisibleAttribute を設定します](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## 参照  
 [相互運用のための .NET 型の要件](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)   
 [アンマネージ コードとの相互運用](../Topic/Interoperating%20with%20Unmanaged%20Code.md)