---
title: "CA1725: パラメーター名は基本宣言と同一でなければなりません | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ParameterNamesShouldMatchBaseDeclaration"
  - "CA1725"
helpviewer_keywords: 
  - "CA1725"
  - "ParameterNamesShouldMatchBaseDeclaration"
ms.assetid: 9b657ab0-fe81-4f4c-9481-ba746988c922
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA1725: パラメーター名は基本宣言と同一でなければなりません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ParameterNamesShouldMatchBaseDeclaration|  
|CheckId|CA1725|  
|分類|Microsoft.Naming|  
|互換性に影響する変更点|あり|  
  
## 原因  
 外部から参照できるメソッド オーバーライドのパラメーターの名前が、メソッドの基本宣言のパラメーター名またはメソッドのインターフェイス宣言のパラメーター名と一致していません。  
  
## 規則の説明  
 オーバーライド階層のパラメーターに対する一貫性のある名前付けによって、メソッド オーバーライドの有用性が高まります。  派生メソッドのパラメーター名が基本宣言のパラメーター名と異なる場合、メソッドが基本メソッドのオーバーライドであるか、またはメソッドの新しいオーバーライドであるかについて混乱が生じる可能性があります。  
  
## 違反の修正方法  
 この規則違反を修正するには、基本宣言に一致するようにパラメーター名を変更します。  この修正は、COM 参照可能メソッドの互換性に影響します。  
  
## 警告を抑制する状況  
 以前に提供済みのライブラリ内の COM 参照可能メソッドの場合を除き、この規則による警告を抑制しないでください。