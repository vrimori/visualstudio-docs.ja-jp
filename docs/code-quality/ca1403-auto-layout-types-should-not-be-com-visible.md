---
title: "CA1403: Auto 配置の型を COM 参照可能にすることはできません | Microsoft Docs"
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
  - "AutoLayoutTypesShouldNotBeComVisible"
  - "CA1403"
helpviewer_keywords: 
  - "CA1403"
  - "AutoLayoutTypesShouldNotBeComVisible"
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1403: Auto 配置の型を COM 参照可能にすることはできません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AutoLayoutTypesShouldNotBeComVisible|  
|CheckId|CA1403|  
|分類|Microsoft.Interoperability|  
|互換性に影響する変更点|あり|  
  
## 原因  
 コンポーネント オブジェクト モデル \(COM: Component Object Model\) から参照可能な値型が、<xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName> に設定された <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> 属性でマークされています。  
  
## 規則の説明  
 <xref:System.Runtime.InteropServices.LayoutKind> レイアウト型は、共通言語ランタイムによって管理されています。  これらの型のレイアウトは .NET Framework のバージョンによって異なる場合があるため、特定のレイアウトを必要とする COM クライアントが動作しなくなる可能性があります。  <xref:System.Runtime.InteropServices.StructLayoutAttribute> 属性が指定されていない場合、C\#、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]、および C\+\+ のコンパイラが <xref:System.Runtime.InteropServices.LayoutKind> レイアウトを値型に指定することに注意してください。  
  
 特にマークされていない限り、すべてのパブリックな非ジェネリック型は、COM 参照可能ですが、すべての非パブリックなジェネリック型は COM 参照不可能です。  ただし、誤った規則違反のレポートを減らすために、この規則では、COM から参照できる型を明示的に示す必要があります。包含アセンブリは、<xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> を `false` に設定してマークし、型は、<xref:System.Runtime.InteropServices.ComVisibleAttribute> を `true` に設定してマークする必要があります。  
  
## 違反の修正方法  
 この規則違反を修正するには、<xref:System.Runtime.InteropServices.StructLayoutAttribute> 属性の値を <xref:System.Runtime.InteropServices.LayoutKind> または <xref:System.Runtime.InteropServices.LayoutKind> に変更するか、型を COM 参照できないようにします。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## 使用例  
 この規則に違反している型と、規則に適合する型を次の例に示します。  
  
 [!CODE [FxCop.Interoperability.AutoLayout#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout#1)]  
  
## 関連規則  
 [CA1408: AutoDual ClassInterfaceType を使用しないでください](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)  
  
## 参照  
 [Introducing the Class Interface](http://msdn.microsoft.com/ja-jp/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [相互運用のための .NET 型の要件](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)   
 [アンマネージ コードとの相互運用](../Topic/Interoperating%20with%20Unmanaged%20Code.md)