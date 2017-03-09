---
title: "CA1411: COM 登録メソッドは参照可能であることはできません | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1411"
  - "ComRegistrationMethodsShouldNotBeVisible"
helpviewer_keywords: 
  - "ComRegistrationMethodsShouldNotBeVisible"
  - "CA1411"
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1411: COM 登録メソッドは参照可能であることはできません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ComRegistrationMethodsShouldNotBeVisible|  
|CheckId|CA1411|  
|分類|Microsoft.Interoperability|  
|互換性に影響する変更点|あり|  
  
## 原因  
 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> 属性または <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> 属性のマークが付けられたメソッドが、外部から参照可能になっています。  
  
## 規則の説明  
 アセンブリをコンポーネント オブジェクト モデル \(COM: Component Object Model\) に登録すると、エントリはアセンブリ内の COM 参照可能なそれぞれの型に対して、レジストリに追加されます。  <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> 属性および <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> 属性のマークが付けられたメソッドは、それぞれ登録および登録解除の実行中に呼び出され、それぞれの型の登録\/登録解除に固有のユーザー コードを実行します。  このコードは、これらのプロセスの外側から呼び出すことができないようにしてください。  
  
## 違反の修正方法  
 この規則違反を修正するには、メソッドのアクセシビリティを `private` または `internal` \([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] の場合は `Friend`\) に変更します。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## 使用例  
 この規則に違反する 2 つのメソッドを次の例に示します。  
  
 [!code-cs[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/CSharp/ca1411-com-registration-methods-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/VisualBasic/ca1411-com-registration-methods-should-not-be-visible_1.vb)]  
  
## 関連規則  
 [CA1410: COM 登録メソッドは一致しなければなりません](../code-quality/ca1410-com-registration-methods-should-be-matched.md)  
  
## 参照  
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>   
 [COM へのアセンブリの登録](../Topic/Registering%20Assemblies%20with%20COM.md)   
 [Regasm.exe \(アセンブリ登録ツール\)](../Topic/Regasm.exe%20\(Assembly%20Registration%20Tool\).md)