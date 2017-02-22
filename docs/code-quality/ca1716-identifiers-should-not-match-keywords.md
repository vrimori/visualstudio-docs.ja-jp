---
title: "CA1716: 識別子はキーワードと同一にすることはできません | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IdentifiersShouldNotMatchKeywords"
  - "CA1716"
helpviewer_keywords: 
  - "IdentifiersShouldNotMatchKeywords"
  - "CA1716"
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1716: 識別子はキーワードと同一にすることはできません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldNotMatchKeywords|  
|CheckId|CA1716|  
|分類|Microsoft.Naming|  
|互換性に影響する変更点|あり|  
  
## 原因  
 名前空間、型、仮想メンバー、またはインターフェイス メンバーの名前が、プログラミング言語で予約済みのキーワードと一致します。  
  
## 規則の説明  
 名前空間、型、仮想メンバー、およびインターフェイス メンバーの識別子は、共通言語ランタイムを対象にする言語で定義されているキーワードと一致しないようにします。  使用している言語とキーワードによっては、コンパイラのエラーや不明確さによってライブラリの操作が困難になります。  
  
 この規則は、以下の言語のキーワードをチェックします。  
  
-   Visual Basic  
  
-   C\#  
  
-   C\+\+\/CLI  
  
 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] キーワードの比較では大文字小文字が区別されず、その他の言語の比較では大文字小文字が区別されます。  
  
## 違反の修正方法  
 キーワードの一覧にない名前を選択します。  
  
## 警告を抑制する状況  
 識別子によって API のユーザーが混乱しないこと、およびライブラリが [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] の使用可能なすべての言語で使用できることを確認できる場合、この規則による警告を抑制できます。