---
title: "CA2123: オーバーライドのリンク確認要求は基本と同様にします | Microsoft Docs"
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
  - "CA2123"
  - "OverrideLinkDemandsShouldBeIdenticalToBase"
helpviewer_keywords: 
  - "CA2123"
  - "OverrideLinkDemandsShouldBeIdenticalToBase"
ms.assetid: 4538ecd5-fc6f-4480-ab00-90b2ce4730db
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2123: オーバーライドのリンク確認要求は基本と同様にします
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverrideLinkDemandsShouldBeIdenticalToBase|  
|CheckId|CA2123|  
|分類|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## 原因  
 パブリック型のパブリック メソッドまたはプロテクト メソッドが、メソッドをオーバーライドするかインターフェイスを実装し、そのインターフェイスまたは仮想メソッドと同じ[リンク確認要求](../Topic/Link%20Demands.md)を持っていません。  
  
## 規則の説明  
 この規則は、メソッドをその基本メソッド \(別の型のインターフェイスまたは仮想メソッド\) とマッチングし、それぞれについてリンク確認要求を比較します。  メソッドと基本メソッドの一方にリンク確認要求があり、もう一方にないとき、違反がレポートされます。  
  
 この規則に違反すると、悪意のある呼び出し元が、保護されていないメソッドを呼び出すだけで、リンク確認要求を省略できます。  
  
## 違反の修正方法  
 この規則違反を修正するには、オーバーライド メソッドまたは実装に同じリンク確認要求を適用します。  それができない場合は、フル アクセス要求でメソッドを設定するか、属性をすべて削除します。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## 使用例  
 この規則のさまざまな違反例を次に示します。  
  
 [!code-cs[FxCop.Security.OverridesAndSecurity#1](../code-quality/codesnippet/CSharp/ca2123-override-link-demands-should-be-identical-to-base_1.cs)]  
  
## 参照  
 [安全なコーディングのガイドライン](../Topic/Secure%20Coding%20Guidelines.md)   
 [リンク確認要求](../Topic/Link%20Demands.md)