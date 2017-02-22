---
title: "CA1726: 適切な用語を使用します | Microsoft Docs"
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
  - "UsePreferredTerms"
  - "CA1726"
helpviewer_keywords: 
  - "UsePreferredTerms"
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1726: 適切な用語を使用します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UsePreferredTerms|  
|CheckId|CA1726|  
|分類|Microsoft.Naming|  
|互換性に影響する変更点|あり – アセンブリで発生した場合<br /><br /> なし – 型パラメーター上で発生した場合|  
  
## 原因  
 外部から参照可能な識別子の名前に含まれている用語に対応する、別の推奨される用語があります。  あるいは、名前に Flag または Flags という語が含まれています。  
  
## 規則の説明  
 この規則では、識別子をトークンとして解析します。  単一のトークン、および隣接する 2 つのトークンの組み合わせが、規則に組み込まれている用語やカスタム ディクショナリの Deprecated セクションの用語と比較されます。  この規則に組み込まれている用語と、その代わりに推奨される用語を次の表に示します。  
  
|廃止された用語|推奨される用語|  
|-------------|-------------|  
|Arent|AreNot|  
|Cancelled|Canceled|  
|Cant|Cannot|  
|ComPlus|EnterpriseServices|  
|Couldnt|CouldNot|  
|Didnt|DidNot|  
|Doesnt|DoesNot|  
|Dont|DoNot|  
|Flag または Flags|代わりになる用語はありません。  使用しないでください。|  
|Hadnt|HadNot|  
|Hasn’t|HadNot|  
|Havent|HaveNot|  
|Indices|Indexes|  
|Isnt|IsNot|  
|LogIn|LogOn|  
|LogOut|LogOff|  
|Shouldnt|ShouldNot|  
|SignOn|SignIn|  
|SignOff|SignOut|  
|Wasnt|WasNot|  
|Werent|WereNot|  
|Wont|WillNot|  
|Wouldnt|WouldNot|  
|Writeable|Writable|  
  
## 違反の修正方法  
 この規則の違反を修正するには、その用語を推奨される用語に置き換えます。  
  
## 警告を抑制する状況  
 識別子の名前に推奨される用語を使用せず、名前が意図的な場合、かつ名前を以前の用語に個別に関連付けている場合にのみ、この規則による警告を抑制してください。  
  
## 関連規則  
 [名前付けに関する警告](../code-quality/naming-warnings.md)