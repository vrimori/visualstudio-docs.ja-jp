---
title: "CA1721: プロパティ名は get メソッドと同一にすることはできません | Microsoft Docs"
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
  - "CA1721"
  - "PropertyNamesShouldNotMatchGetMethods"
helpviewer_keywords: 
  - "CA1721"
  - "PropertyNamesShouldNotMatchGetMethods"
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1721: プロパティ名は get メソッドと同一にすることはできません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PropertyNamesShouldNotMatchGetMethods|  
|CheckId|CA1721|  
|分類|Microsoft.Naming|  
|互換性に影響する変更点|あり|  
  
## 原因  
 パブリック メンバーまたはプロテクト メンバーの名前が、"Get" から始まります。または、パブリック プロパティまたはプロテクト プロパティの名前と一致します。  たとえば、"GetColor" というメソッドを含む型と "Color" というプロパティがあると、この規則に違反します。  
  
## 規則の説明  
 get メソッドとプロパティは、機能を明確に区別できる名前にします。  
  
 名前付け規則では、共通言語ランタイムをターゲットとするライブラリの統一的な名前の付け方が規定されています。  これにより、新しいソフトウェア ライブラリを習得するまでの時間を短縮でき、マネージ コード開発の専門家によってライブラリが開発されたという信頼を顧客に与えることができます。  
  
## 違反の修正方法  
 "Get" で始まるメソッド名に一致しないように、名前を変更します。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
> [!NOTE]
>  Get メソッドが IExtenderProvider インターフェイスの実装によって呼び出された場合は、この警告は除外されることがあります。  
  
## 使用例  
 この規則に違反するメソッドとプロパティを含む例を次に示します。  
  
 [!CODE [FxCop.Naming.GetMethod#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Naming.GetMethod#1)]  
  
## 関連規則  
 [CA1024: 適切な場所にプロパティを使用します](../code-quality/ca1024-use-properties-where-appropriate.md)