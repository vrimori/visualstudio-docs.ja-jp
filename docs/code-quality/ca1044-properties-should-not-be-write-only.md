---
title: "CA1044: プロパティを書き込み専用にすることはできません | Microsoft Docs"
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
  - "PropertiesShouldNotBeWriteOnly"
  - "CA1044"
helpviewer_keywords: 
  - "CA1044"
  - "PropertiesShouldNotBeWriteOnly"
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1044: プロパティを書き込み専用にすることはできません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PropertiesShouldNotBeWriteOnly|  
|CheckId|CA1044|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## 原因  
 パブリック プロパティまたはプロテクト プロパティに set アクセサーはありますが、get アクセサーがありません。  
  
## 規則の説明  
 get アクセサーでプロパティに読み取りアクセスが可能になり、set アクセサーで書き込みアクセスが可能になります。  読み取り専用のプロパティは許容され、必要な場合もよくありますが、書き込み専用のプロパティを使用することはデザインのガイドラインで禁止されています。  これは、値を設定できてもその値を参照できず、セキュリティが確保されないためです。  また、読み取りアクセスがないと、共有オブジェクトのステータスを参照できないため、実用性が制限されます。  
  
## 違反の修正方法  
 この規則違反を修正するには、プロパティに get アクセサーを追加します。  または、書き込み専用のプロパティの動作が必要な場合、このプロパティをメソッドに変換する方法を検討します。  
  
## 警告を抑制する状況  
 この規則による警告を抑制しないことを強くお勧めします。  
  
## 使用例  
 次の例では、`BadClassWithWriteOnlyProperty` は書き込み専用プロパティがある型です。  `GoodClassWithReadWriteProperty` に修正後のコードが格納されます。  
  
 [!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/VisualBasic/ca1044-properties-should-not-be-write-only_1.vb)]
 [!code-cs[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/CSharp/ca1044-properties-should-not-be-write-only_1.cs)]