---
title: "CA1412: ComSource インターフェイスを IDispatch として設定します | Microsoft Docs"
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
  - "MarkComSourceInterfacesAsIDispatch"
  - "CA1412"
helpviewer_keywords: 
  - "CA1412"
  - "MarkComSourceInterfacesAsIDispatch"
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1412: ComSource インターフェイスを IDispatch として設定します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkComSourceInterfacesAsIDispatch|  
|CheckId|CA1412|  
|分類|Microsoft.Interoperability|  
|互換性に影響する変更点|あり|  
  
## 原因  
 型が <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> 属性によってマークされていますが、1 つ以上の指定されたインターフェイスが `InterfaceIsDispatch` 値に設定された <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> 属性によってマークされていません。  
  
## 規則の説明  
 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> は、クラスがコンポーネント オブジェクト モデル \(COM: Component Object Model\) クライアントに公開するイベント インターフェイスを識別するために使用されます。  Visual Basic 6 COM クライアントがイベント通知を受信できるように、これらのインターフェイスは `InterfaceIsIDispatch` として公開する必要があります。  既定では、インターフェイスが <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> 属性によってマークされていない場合、デュアル インターフェイスとして公開されます。  
  
## 違反の修正方法  
 この規則の違反を修正するには、<xref:System.Runtime.InteropServices.InterfaceTypeAttribute> 属性を追加または変更して、<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> 属性によって指定されたすべてのインターフェイスに対して、値が InterfaceIsIDispatch に設定されるようにします。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## 使用例  
 インターフェイスの 1 つがこの規則に違反しているクラスを次の例に示します。  
  
 [!code-cs[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/CSharp/ca1412-mark-comsource-interfaces-as-idispatch_1.cs)]
 [!code-vb[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/VisualBasic/ca1412-mark-comsource-interfaces-as-idispatch_1.vb)]  
  
## 関連規則  
 [CA1408: AutoDual ClassInterfaceType を使用しないでください](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)  
  
## 参照  
 [How to: Raise Events Handled by a COM Sink](http://msdn.microsoft.com/ja-jp/7c9944b2-e951-4c3e-a0a1-59b2ae37d7fd)   
 [アンマネージ コードとの相互運用](../Topic/Interoperating%20with%20Unmanaged%20Code.md)