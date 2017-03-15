---
title: "CA1032: 標準例外コンストラクターを実装します | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1032"
  - "ImplementStandardExceptionConstructors"
helpviewer_keywords: 
  - "CA1032"
  - "ImplementStandardExceptionConstructors"
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA1032: 標準例外コンストラクターを実装します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ImplementStandardExceptionConstructors|  
|CheckId|CA1032|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|なし|  
  
## 原因  
 型が <xref:System.Exception?displayProperty=fullName> を拡張し、必要なコンストラクターのすべてを宣言していません。  
  
## 規則の説明  
 例外型では、次のコンストラクターを実装する必要があります。  
  
-   public NewException\(\)  
  
-   public NewException\(string\)  
  
-   public NewException\(string, Exception\)  
  
-   protected または private NewException\(SerializationInfo, StreamingContext\)  
  
 コンストラクターを完全に宣言していないと、例外を正しく処理するのが困難になります。  たとえば、シグネチャ `NewException(string, Exception)` を持つコンストラクターは、他の例外によって発生する例外を作成するときに使用されます。  このコンストラクターがないと、内部に \(入れ子になった\) 例外を含むカスタムの例外のインスタンスを作成してスローすることができなくなります。これは、マネージ コードに必要な処理です。  最初の 3 つの例外コンストラクターは、規約ではパブリックです。  4 つ目のコンストラクターは、シールされていないクラスではプロテクトであり、シールされているクラスではプライベートです。  詳細については、「[CA2229: シリアル化コンストラクターを実装します](../code-quality/ca2229-implement-serialization-constructors.md)」を参照してください。  
  
## 違反の修正方法  
 この規則違反を修正するには、例外に必要なコンストラクターを追加し、適切なアクセシビリティを指定します。  
  
## 警告を抑制する状況  
 パブリック コンストラクターに異なるアクセス レベルを指定することでこの違反が発生する場合は、この規則による警告を抑制しても安全です。  
  
## 使用例  
 この規則に違反する例外型と、適切に実装した例外型を次の例に示します。  
  
 [!code-cs[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]