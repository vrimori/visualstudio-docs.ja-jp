---
title: "CA1809: ローカルを使用しすぎないでください | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1809"
  - "AvoidExcessiveLocals"
helpviewer_keywords: 
  - "AvoidExcessiveLocals"
  - "CA1809"
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA1809: ローカルを使用しすぎないでください
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidExcessiveLocals|  
|CheckId|CA1809|  
|分類|Microsoft.Performance|  
|互換性に影響する変更点|なし|  
  
## 原因  
 メンバーに含まれるローカル変数の数が 64 個を超えています。その一部はコンパイラにより生成されている可能性があります。  
  
## 規則の説明  
 パフォーマンス最適化の一般的な方法として、メモリではなくプロセッサのレジスタに値を格納する方法があります。これは値の*レジスタ格納*と呼ばれます。  共通言語ランタイムでは、最大 64 個のローカル変数をレジスタ格納することが想定されています。  レジスタ格納されなかった変数は、スタックに配置されるため、操作を行う前にレジスタに移動する必要があります。  すべてのローカル変数をレジスタ格納できるようにするには、ローカル変数の数を 64 個に制限します。  
  
## 違反の修正方法  
 この規則の違反を修正するには、64 個を超えるローカル変数を使用しないように実装をリファクタリングします。  
  
## 警告を抑制する状況  
 パフォーマンスに問題がない場合は、この規則による警告を抑制したり、規則を無効にしたりしても安全です。  
  
## 関連規則  
 [CA1804: 使用されていないローカルを削除します](../code-quality/ca1804-remove-unused-locals.md)