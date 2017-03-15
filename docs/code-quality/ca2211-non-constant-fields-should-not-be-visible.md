---
title: "CA2211: 非定数フィールドは表示されません | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2211"
  - "NonConstantFieldsShouldNotBeVisible"
helpviewer_keywords: 
  - "CA2211"
  - "NonConstantFieldsShouldNotBeVisible"
ms.assetid: e1e42c40-0acd-4312-af29-70133739a304
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA2211: 非定数フィールドは表示されません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|NonConstantFieldsShouldNotBeVisible|  
|CheckId|CA2211|  
|分類|Microsoft.Usage|  
|互換性に影響する変更点|あり|  
  
## 原因  
 パブリックまたはプロテクトの静的フィールドが、定数でも読み取り専用でもありません。  
  
## 規則の説明  
 定数でも読み取り専用でもない静的フィールドは、スレッド セーフではありません。  このようなフィールドへのアクセスは、慎重に制御してください。また、クラス オブジェクトへのアクセスを同期するには、高度なプログラミング技術が必要です。  この制御は習得が困難なスキルで、このようなオブジェクトのテストには固有の難しさがあるため、静的フィールドは変化しないデータを格納するときに使用することが最適です。  この規則はライブラリに適用されます。アプリケーションではフィールドを公開しないでください。  
  
## 違反の修正方法  
 この規則違反を修正するには、静的フィールドを定数または読み取り専用にします。  それができない場合は、型を再デザインし、別の機構を使用します。たとえば、スレッド セーフのプロパティなどで、基になるフィールドに対してスレッド セーフのアクセスを管理する方法です。  ロックの競合やデッドロックなどの問題は、ライブラリのパフォーマンスと動作に影響を及ぼす可能性があります。  
  
## 警告を抑制する状況  
 アプリケーションを開発しているため、静的フィールドを含む型に対してフル コントロール アクセス権を持つ場合は、この規則による警告を抑制しても安全です。  ライブラリをデザインしている場合は、この規則による警告を抑制しないでください。定数ではない静的フィールドを使用すると、ライブラリを適切に開発することが困難になります。  
  
## 使用例  
 この規則に違反する型を次の例に示します。  
  
 [!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/VisualBasic/ca2211-non-constant-fields-should-not-be-visible_1.vb)]
 [!code-cs[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/CSharp/ca2211-non-constant-fields-should-not-be-visible_1.cs)]