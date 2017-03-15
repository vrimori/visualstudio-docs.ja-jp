---
title: "CA1408: AutoDual ClassInterfaceType を使用しないでください | Microsoft Docs"
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
  - "DoNotUseAutoDualClassInterfaceType"
  - "CA1408"
helpviewer_keywords: 
  - "CA1408"
  - "DoNotUseAutoDualClassInterfaceType"
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1408: AutoDual ClassInterfaceType を使用しないでください
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotUseAutoDualClassInterfaceType|  
|CheckId|CA1408|  
|分類|Microsoft.Interoperability|  
|互換性に影響する変更点|あり|  
  
## 原因  
 コンポーネント オブジェクト モデル \(COM: Component Object Model\) から参照可能な型が、<xref:System.Runtime.InteropServices.ClassInterfaceType> の `AutoDual` 値に設定された <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 属性でマークされています。  
  
## 規則の説明  
 デュアル インターフェイスを使用する型を使用することで、クライアントを特定のインターフェイス レイアウトに対応付けることができます。  将来のバージョンで、この型またはその基本型のレイアウトに変更が加えられると、インターフェイスに対応付けられた COM クライアントが切り離されます。  既定では、<xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 属性が指定されていない場合、ディスパッチのみのインターフェイスが使用されます。  
  
 特にマークされていない限り、すべてのパブリックな非ジェネリック型は、COM 参照可能ですが、すべての非パブリックなジェネリック型は COM 参照不可能です。  
  
## 違反の修正方法  
 この規則違反を修正するには、<xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 属性の値を <xref:System.Runtime.InteropServices.ClassInterfaceType> の `None` に変更し、インターフェイスを明示的に定義します。  
  
## 警告を抑制する状況  
 この型のレイアウトとその基本型のレイアウトが将来のバージョンで変更されないことが確実である場合を除いて、この規則による警告は抑制しないでください。  
  
## 使用例  
 この規則に違反するクラスと、明示的なインターフェイスを使用するクラスの再宣言を次の例に示します。  
  
 [!code-cs[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/CSharp/ca1408-do-not-use-autodual-classinterfacetype_1.cs)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/VisualBasic/ca1408-do-not-use-autodual-classinterfacetype_1.vb)]  
  
## 関連規則  
 [CA1403: Auto 配置の型を COM 参照可能にすることはできません](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)  
  
 [CA1412: ComSource インターフェイスを IDispatch として設定します](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)  
  
## 参照  
 [Introducing the Class Interface](http://msdn.microsoft.com/ja-jp/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [相互運用のための .NET 型の要件](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)   
 [アンマネージ コードとの相互運用](../Topic/Interoperating%20with%20Unmanaged%20Code.md)