---
title: "CA2149: 透過的メソッドは、ネイティブ コード内に呼び出しを行ってはならない | Microsoft Docs"
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
  - "CA2149"
ms.assetid: 28951bd7-f3db-4871-99aa-bad68d1ead80
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2149: 透過的メソッドは、ネイティブ コード内に呼び出しを行ってはならない
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsMustNotCallNativeCode|  
|CheckId|CA2149|  
|分類|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## 原因  
 メソッドは、P\/Invoke などのメソッド スタブを使用してネイティブ関数を呼び出します。  
  
## 規則の説明  
 この規則は、P\/Invoke などを使用してネイティブ コードを直接呼び出すすべての透過的メソッドに対して適用されます。  この規則に違反すると、レベル 2 の透過性モデルで例外 <xref:System.MethodAccessException> が発生し、レベル 1 の透過性モデルで <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> に対するフル アクセス要求が発生します。  
  
## 違反の修正方法  
 この規則違反を修正するには、ネイティブ コードを呼び出すメソッドに <xref:System.Security.SecurityCriticalAttribute> 属性または <xref:System.Security.SecuritySafeCriticalAttribute> 属性を適用します。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## 使用例  
 [!CODE [FxCop.Security.CA2149.TransparentMethodsMustNotCallNativeCode#1](../CodeSnippet/VS_Snippets_CodeAnalysis/fxcop.security.ca2149.transparentmethodsmustnotcallnativecode#1)]