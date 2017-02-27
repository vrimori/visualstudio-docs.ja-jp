---
title: "CA1823: 使用されていないプライベート フィールドを使用しません | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidUnusedPrivateFields"
  - "CA1823"
helpviewer_keywords: 
  - "AvoidUnusedPrivateFields"
  - "CA1823"
ms.assetid: 614f94f6-0dc7-430f-8124-cb889a4a720f
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA1823: 使用されていないプライベート フィールドを使用しません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidUnusedPrivateFields|  
|CheckId|CA1823|  
|分類|Microsoft.Performance|  
|互換性に影響する変更点|なし|  
  
## 原因  
 この規則は、コード内にプライベート フィールドが存在しているが、コード パスで使用されていない場合に報告されます。  
  
## 規則の説明  
 アセンブリ内でアクセスされていないと思われるプライベート フィールドが検出されました。  
  
## 違反の修正方法  
 この規則違反を修正するには、そのフィールドを削除するか、そのフィールドを使用するコードを追加します。  
  
## 警告を抑制する状況  
 この規則による警告を抑制しても安全です。  
  
## 関連規則  
 [CA1812: インスタンス化されていない内部クラスを使用しないでください](../Topic/CA1812:%20Avoid%20uninstantiated%20internal%20classes.md)  
  
 [CA1801: 使用されていないパラメーターを再確認します](../Topic/CA1801:%20Review%20unused%20parameters.md)  
  
 [CA1804: 使用されていないローカルを削除します](../code-quality/ca1804-remove-unused-locals.md)  
  
 [CA1811: 呼び出されていないプライベート コードを使用しません](../code-quality/ca1811-avoid-uncalled-private-code.md)