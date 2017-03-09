---
title: "DLL のクライアント アプリケーションの数が多すぎます | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrID47"
ms.assetid: 4b87780b-67ad-4c96-9253-db954a751dad
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# DLL のクライアント アプリケーションの数が多すぎます
[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] のダイナミック リンク ライブラリ \(DLL\) にアクセスできるホスト アプリケーションの数は限られています。 使用しているアプリケーションと、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ホスト \(その一部は使用しているアプリケーションによってアクセスされる可能性があります\) であるその他のアプリケーションとがすべて同時に [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] DLL にアクセスしようとしています。  
  
### このエラーを解決するには  
  
-   [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] にアクセスする動作中のアプリケーションの数を減らします。  
  
## 参照  
 [Error Types](/dotnet/visual-basic/programming-guide/language-features/error-types)