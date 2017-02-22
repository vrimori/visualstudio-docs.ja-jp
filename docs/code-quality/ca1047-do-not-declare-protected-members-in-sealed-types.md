---
title: "CA1047: Sealed 型の保護されたメンバーを宣言しません | Microsoft Docs"
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
  - "DoNotDeclareProtectedMembersInSealedTypes"
  - "CA1047"
helpviewer_keywords: 
  - "CA1047"
  - "DoNotDeclareProtectedMembersInSealedTypes"
ms.assetid: 829033b5-a9d8-4f26-a719-45494c9dd035
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1047: Sealed 型の保護されたメンバーを宣言しません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDeclareProtectedMembersInSealedTypes|  
|CheckId|CA1047|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|なし|  
  
## 原因  
 パブリック型が `sealed` \(Visual Basic では `NotInheritable`\) であり、プロテクト メンバーまたは入れ子にされたプロテクト型が宣言されています。  <xref:System.Object.Finalize%2A> メソッドの場合、このパターンに従いますが、この規則による違反はレポートされません。  
  
## 規則の説明  
 型でプロテクト メンバーを宣言するのは、継承する型からメンバーにアクセスまたはオーバーライドできるようにするためです。  定義によってシールされた型から継承することはできません。シールとは、シールされた型のプロテクト メソッドを呼び出すことができないということを意味します。  
  
 C\# コンパイラでは、このエラーに対して警告が発行されます。  
  
## 違反の修正方法  
 この規則違反を修正するには、メンバーのアクセス レベルをプライベートにするか、型を継承できるようにします。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  型を現在のままにすると保守の問題が発生し、何も利点はありません。  
  
## 使用例  
 この規則に違反する型を次の例に示します。  
  
 [!code-vb[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/VisualBasic/ca1047-do-not-declare-protected-members-in-sealed-types_1.vb)]
 [!code-cs[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/CSharp/ca1047-do-not-declare-protected-members-in-sealed-types_1.cs)]