---
title: "CA1724: 型名は名前空間と同一にすることはできません | Microsoft Docs"
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
  - "TypeNamesShouldNotMatchNamespaces"
  - "CA1724"
helpviewer_keywords: 
  - "TypeNamesShouldNotMatchNamespaces"
  - "CA1724"
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1724: 型名は名前空間と同一にすることはできません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypeNamesShouldNotMatchNamespaces|  
|CheckId|CA1724|  
|分類|Microsoft.Naming|  
|互換性に影響する変更点|あり|  
  
## 原因  
 大文字と小文字を区別しない比較で、型の名前が [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 名前空間の名前と一致します。  
  
## 規則の説明  
 型の名前は、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] クラス ライブラリで定義されている名前空間の名前と一致しないようにする必要があります。  この規則に違反すると、ライブラリが使いづらくなります。  
  
## 違反の修正方法  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] クラス ライブラリの名前空間の名前と一致しない型の名前を選択します。  
  
## 警告を抑制する状況  
 新たに開発する場合、この規則による警告を抑制する必要がある状況は発生しません。  警告を抑制する前に、一致する名前によってライブラリのユーザーの間にどのような混乱が生じる可能性があるかを慎重に検討する必要があります。  ライブラリを同梱する場合、この規則による警告の抑制が必要となることもあります。