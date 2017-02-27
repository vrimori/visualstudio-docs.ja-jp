---
title: "CA1050: 名前空間で型を宣言します | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1050"
  - "DeclareTypesInNamespaces"
helpviewer_keywords: 
  - "CA1050"
  - "DeclareTypesInNamespaces"
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1050: 名前空間で型を宣言します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DeclareTypesInNamespaces|  
|CheckId|CA1050|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## 原因  
 パブリック型またはプロテクト型が、名前付き名前空間のスコープ外で定義されています。  
  
## 規則の説明  
 型を名前空間内で宣言するのは、名前が衝突しないようにするためと、関連する型をオブジェクト階層形式で編成するためです。  名前付き名前空間の外部にある型は、コードで参照できないグローバル名前空間に含まれます。  
  
## 違反の修正方法  
 この規則違反を修正するには、名前空間で型を宣言します。  
  
## 警告を抑制する状況  
 この規則による警告を抑制する必要はまったくありませんが、そのアセンブリを他のアセンブリと共に使用しない場合は、抑制しても安全です。  
  
## 使用例  
 名前空間の外部で不適切に宣言された型と、名前空間内に同じ名前で宣言された型を含むライブラリを次の例に示します。  
  
 [!code-cs[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_1.cs)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_1.vb)]  
  
## 使用例  
 次のアプリケーションでは、上記で定義したライブラリを使用します。  `Test` という名前が名前空間で修飾されていないと、名前空間の外部で宣言された型が作成されることに注意してください。  また、`Goodspace` の `Test` 型にアクセスするには、名前空間の名前が必要です。  
  
 [!CODE [FxCop.Design.TestTypesLive#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive#1)]