---
title: "CA2230: 可変引数に対して param を使用します | Microsoft Docs"
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
  - "UseParamsForVariableArguments"
  - "CA2230"
helpviewer_keywords: 
  - "CA2230"
  - "UseParamsForVariableArguments"
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2230: 可変引数に対して param を使用します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseParamsForVariableArguments|  
|CheckId|CA2230|  
|分類|Microsoft.Usage|  
|互換性に影響する変更点|あり|  
  
## 原因  
 パブリック型またはプロテクト型に、`VarArgs` 呼び出し規約を使用するパブリック メソッドまたはプロテクト メソッドが含まれます。  
  
## 規則の説明  
 `VarArgs` 呼び出し規約は、可変個のパラメーターを使用する特定のメソッド定義で使用されます。  `VarArgs` 呼び出し規約を使用するメソッドは、共通言語仕様 \(CLS\) 準拠ではありません。また、プログラミング言語が異なるとアクセスできないことがあります。  
  
 C\# では、メソッドのパラメーター リストが `__arglist` キーワードで終わるときに、`VarArgs` 呼び出し規約を使用します。  Visual Basic は、`VarArgs` 呼び出し規約をサポートしていません。また、Visual C\+\+ では、`...` の省略表記を使用するアンマネージ コードでのみ、使用できます。  
  
## 違反の修正方法  
 C\# でこの規則違反を修正するには、`__arglist` ではなく [params](/dotnet/csharp/language-reference/keywords/params) キーワードを使用します。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## 使用例  
 この規則に違反しているメソッドと、規則に適合するメソッドを次の例に示します。  
  
 [!code-cs[FxCop.Usage.UseParams#1](../code-quality/codesnippet/CSharp/ca2230-use-params-for-variable-arguments_1.cs)]  
  
## 参照  
 <xref:System.Reflection.CallingConventions?displayProperty=fullName>   
 [言語への非依存性、および言語非依存コンポーネント](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)