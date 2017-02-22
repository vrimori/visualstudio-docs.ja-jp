---
title: "CA1506: クラス結合度を大きくしすぎないでください | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidExcessiveClassCoupling"
  - "CA1506"
helpviewer_keywords: 
  - "AvoidExcessiveClassCoupling"
  - "CA1506"
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1506: クラス結合度を大きくしすぎないでください
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidExcessiveClassCoupling|  
|CheckId|CA1506|  
|分類|Microsoft.Maintainability|  
|互換性に影響する変更点|あり|  
  
## 原因  
 型またはメソッドが他の多数の型と結合されています。  
  
## 規則の説明  
 この規則は、型またはメソッドに含まれる一意の型参照の数をカウントすることによって、クラス結合度を計測します。  
  
 クラス結合度の高い型およびメソッドは、管理が困難になることがあります。  結合度が低く、連携性が高い型およびメソッドを使用することをお勧めします。  
  
## 違反の修正方法  
 この違反を修正するには、結合している型の数を減らすように、型またはメソッドのデザインを変更します。  
  
## 警告を抑制する状況  
 他の型への依存関係が多くても、型またはメソッドが保守しやすいと考えられる場合は、この警告を除外してください。  
  
## 参照  
 [保守性の警告](../code-quality/maintainability-warnings.md)   
 [マネージ コードの複雑さと保守性の測定](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)