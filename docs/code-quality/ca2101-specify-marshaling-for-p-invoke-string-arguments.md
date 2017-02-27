---
title: "CA2101: P/Invoke 文字列引数に対してマーシャリングを指定します | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SpecifyMarshalingForPInvokeStringArguments"
  - "CA2101"
helpviewer_keywords: 
  - "CA2101"
  - "SpecifyMarshalingForPInvokeStringArguments"
ms.assetid: 9d1abfc3-d320-41e0-9f6e-60cefe6ffe1b
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA2101: P/Invoke 文字列引数に対してマーシャリングを指定します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SpecifyMarshalingForPInvokeStringArguments|  
|CheckId|CA2101|  
|分類|Microsoft.Globalization|  
|互換性に影響する変更点|なし|  
  
## 原因  
 プラットフォーム呼び出しメンバーが、部分信頼の呼び出し元を許可し、文字列パラメーターを持ち、さらにその文字列を明示的にマーシャリングしていません。  
  
## 規則の説明  
 Unicode を ANSI に変換するときに、すべての Unicode 文字を特定の ANSI コード ページで表すことができないことがあります。  *最適マッピング*は、表すことのできない文字を別の文字に置き換えることでこの問題を解決しようとします。  この機能を使用すると、選択される文字を制御できないため、セキュリティ上の脆弱性につながる可能性があります。  たとえば、悪意のあるコードで、特定のコード ページに存在しない文字を含む Unicode 文字列が意図的に作成されることが考えられます。このような文字は、".." や "\/" など、ファイル システムの特殊文字に変換されます。  特殊文字のセキュリティ チェックは、文字列が ANSI に変換される前に行われることが多いことにも注意してください。  
  
 最適マッピングは、アンマネージの変換である WChar から MByte の場合に既定です。  最適マッピングを明示的に無効にしないと、この問題が原因で、セキュリティ上の脆弱性のあるコードになる可能性があります。  
  
## 違反の修正方法  
 この規則違反を修正するには、文字列のデータ型を明示的にマーシャリングします。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## 使用例  
 この規則に違反するメソッドを次の例に示します。また、違反の修正例も示します。  
  
 [!code-cs[FxCop.Security.PinvokeAnsiUnicode#1](../code-quality/codesnippet/CSharp/ca2101-specify-marshaling-for-p-invoke-string-arguments_1.cs)]