---
title: "CA2106: アサートをセキュリティで保護します | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2106"
  - "SecureAsserts"
helpviewer_keywords: 
  - "CA2106"
  - "SecureAsserts"
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2106: アサートをセキュリティで保護します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SecureAsserts|  
|CheckId|CA2106|  
|分類|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## 原因  
 メソッドによってアクセス許可がアサートされますが、呼び出し元に対してセキュリティ チェックが実行されていません。  
  
## 規則の説明  
 セキュリティ チェックを実行せずにセキュリティ アクセス許可をアサートすると、悪用される可能性があるセキュリティの弱点がコード内に残る場合があります。  セキュリティ アクセス許可がアサートされると、セキュリティ スタック ウォークが停止します。  呼び出し元にセキュリティ チェックを実行せずにアクセス許可をアサートすると、呼び出し元から作成者のアクセス許可を使用して間接的にコードを実行できる場合があります。  セキュリティ チェックを実行せずにアサートすることは、アサートが有害な方法で利用できない場合に限り許されます。  呼び出すコードが無害であるか、呼び出すコードにユーザーが任意の情報を渡すことができない場合、アサートは無害です。  
  
## 違反の修正方法  
 この規則違反を修正するには、メソッドまたは宣言されている型にセキュリティ確認要求を追加します。  
  
## 警告を抑制する状況  
 セキュリティの確認を慎重に行った後でのみ、この規則による警告を抑制してください。  
  
## 参照  
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>   
 [安全なコーディングのガイドライン](../Topic/Secure%20Coding%20Guidelines.md)