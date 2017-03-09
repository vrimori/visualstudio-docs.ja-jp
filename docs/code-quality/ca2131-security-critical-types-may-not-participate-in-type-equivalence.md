---
title: "CA2131: セキュリティ上重要な型は型等価性に参加してはならない | Microsoft Docs"
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
  - "CA2131"
ms.assetid: 4170f3b1-6086-430d-8fba-837d5538c573
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2131: セキュリティ上重要な型は型等価性に参加してはならない
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CriticalTypesMustNotParticipateInTypeEquivalence|  
|CheckId|CA2131|  
|分類|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## 原因  
 データ型は型の等価性に関与し、型自身、または型のメンバーあるいはフィールドのいずれかに対して <xref:System.Security.SecurityCriticalAttribute> 属性が適用されます。  
  
## 規則の説明  
 この規則は、すべての重要な型、または型の等価性に関与する重要なメソッドあるいはフィールドが定義されたすべての型に対して適用されます。  こうした型が CLR によって検出されると、CLR による型の読み込みが失敗し、実行時に <xref:System.TypeLoadException> が発生します。  通常は、tlbimp やコンパイラによって型の等価性を実装するのではなく、ユーザーが手動で実装した場合に、この規則が適用されます。  
  
## 違反の修正方法  
 この規則違反を修正するには、SecurityCritical 属性を削除します。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## 使用例  
 次の例では、インターフェイス、メソッド、およびフィールドに対してこの規則が適用されます。  
  
 [!code-cs[FxCop.Security.CA2131.CriticalTypesMustNotParticipateInTypeEquivalence#1](../code-quality/codesnippet/CSharp/ca2131-security-critical-types-may-not-participate-in-type-equivalence_1.cs)]  
  
## 参照  
 [透過的セキュリティ コード、レベル 2](../Topic/Security-Transparent%20Code,%20Level%202.md)