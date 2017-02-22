---
title: "CA1719: パラメーター名はメンバー名と同一にすることはできません | Microsoft Docs"
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
  - "ParameterNamesShouldNotMatchMemberNames"
  - "CA1719"
helpviewer_keywords: 
  - "CA1719"
  - "ParameterNamesShouldNotMatchMemberNames"
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1719: パラメーター名はメンバー名と同一にすることはできません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ParameterNamesShouldNotMatchMemberNames|  
|CheckId|CA1719|  
|分類|Microsoft.Naming|  
|互換性に影響する変更点|あり|  
  
## 原因  
 外部から参照できるメンバーの名前が、大文字と小文字は区別しない比較方法で、そのパラメーターの名前と一致します。  
  
## 規則の説明  
 パラメーターはパラメーターの意味、メンバーはメンバーの意味を伝える名前にします。  この 2 つの名前が一致するデザインは、まれにしか見られません。  パラメーターにメンバーと同じ名前を付けるとわかりづらくなり、ライブラリの操作が難しくなります。  
  
## 違反の修正方法  
 メンバー名と一致しないパラメーター名を選択します。  
  
## 警告を抑制する状況  
 新たに開発する場合、この規則による警告を抑制する必要がある状況は発生しません。  ライブラリを同梱する場合、この規則による警告の抑制が必要となることもあります。  
  
## 関連規則  
 [CA1709: 識別子では、大文字と小文字が正しく区別されなければなりません](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: 識別子は、大文字と小文字の区別以外にも相違していなければなりません](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707: 識別子はアンダースコアを含むことはできません](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)