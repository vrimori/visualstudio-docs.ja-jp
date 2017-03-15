---
title: "CA1722: 識別子は不適切なプレフィックスを含むことはできません。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IdentifiersShouldNotHaveIncorrectPrefix"
  - "CA1722"
helpviewer_keywords: 
  - "CA1722"
  - "IdentifiersShouldNotHaveIncorrectPrefix"
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA1722: 識別子は不適切なプレフィックスを含むことはできません。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldNotHaveIncorrectPrefix|  
|CheckId|CA1722|  
|分類|Microsoft.Naming|  
|互換性に影響する変更点|あり|  
  
## 原因  
 識別子のプレフィックスが不適切です。  
  
## 規則の説明  
 規則では、特定のプログラミング要素にのみ、固有のプレフィックスで始まる名前を付けることができます。  
  
 型名に固有のプレフィックスはありません。また、"C" を先頭に付けることはできません。  この規則では、"CMyClass" などの型名に対して違反をレポートします。"Cache" などの型名の場合、違反をレポートしません。  
  
 名前付け規則では、共通言語ランタイムをターゲットとするライブラリの統一的な名前の付け方が規定されています。  これにより、新しいソフトウェア ライブラリを習得するまでの時間を短縮でき、マネージ コード開発の専門家によってライブラリが開発されたという信頼を顧客に与えることができます。  
  
## 違反の修正方法  
 識別子からプレフィックスを削除します。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## 関連規則  
 [CA1715: 識別子は正しいプレフィックスを含んでいなければなりません](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)