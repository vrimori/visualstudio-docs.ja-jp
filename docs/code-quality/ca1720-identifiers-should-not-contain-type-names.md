---
title: "CA1720: 識別子には型名を含めないでください | Microsoft Docs"
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
  - "CA1720"
  - "IdentifiersShouldNotContainTypeNames"
helpviewer_keywords: 
  - "IdentifiersShouldNotContainTypeNames"
  - "CA1720"
ms.assetid: c95ee48f-f23a-45f0-ac9e-a3c1ecfabdea
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1720: 識別子には型名を含めないでください
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldNotContainTypeNames|  
|CheckId|CA1720|  
|分類|Microsoft.Naming|  
|互換性に影響する変更点|あり|  
  
## 原因  
 外部から参照できるメンバーのパラメーター名に、データ型の名前が含まれます。  
  
 または  
  
 外部から参照できるメンバーの名前に、言語固有のデータ型名が含まれます。  
  
## 規則の説明  
 パラメーターとメンバーの名前では、パラメーターとメンバーの型ではなく意味を伝えるようにします。パラメーターとメンバーの型は、開発ツールで表示されるためです。  メンバー名でデータ型名を使用する必要がある場合は、言語固有の型名ではなく、言語に依存しない型名を使用します。  たとえば、C\# の型名である "int" ではなく、言語に依存しないデータ型名の "Int32" を使用します。  
  
 パラメーター名またはメンバー名の各トークンは、大文字と小文字を区別しない方法で、次の言語固有のデータ型名が含まれているかどうかチェックされます。  
  
-   Bool  
  
-   WChar  
  
-   Int8  
  
-   UInt8  
  
-   Short  
  
-   UShort  
  
-   Int  
  
-   UInt  
  
-   Integer  
  
-   UInteger  
  
-   Long  
  
-   ULong  
  
-   Unsigned  
  
-   Signed  
  
-   Float  
  
-   Float32  
  
-   Float64  
  
 さらに、パラメーター名は、大文字と小文字を区別しない方法で、次の言語に依存しないデータ型名が含まれているかどうかもチェックされます。  
  
-   オブジェクト  
  
-   Obj  
  
-   Boolean  
  
-   Char  
  
-   String  
  
-   SByte  
  
-   Byte  
  
-   UByte  
  
-   Int16  
  
-   UInt16  
  
-   Int32  
  
-   UInt32  
  
-   Int64  
  
-   UInt64  
  
-   IntPtr  
  
-   Ptr  
  
-   ポインター  
  
-   UInptr  
  
-   UPtr  
  
-   UPointer  
  
-   Single  
  
-   Double  
  
-   10 進数  
  
-   Guid  
  
## 違反の修正方法  
 **パラメーターの場合**  
  
 パラメーター名のデータ型の識別子を、そのパラメーターの意味をよく表す用語、または "value" などの汎用的な用語で置き換えます。  
  
 **メンバーの場合**  
  
 メンバー名の言語固有のデータ型の識別子を、そのメンバーの意味をよく表す、言語に依存しない用語、または "value" などの汎用的な用語で置き換えます。  
  
## 警告を抑制する状況  
 型に基づくパラメーター名およびメンバー名の方が適切な場合もあります。  ただし、新たに開発する場合、この規則による警告を抑制する必要がある状況は発生しません。  以前に提供済みのライブラリの場合は、この規則による警告の抑制が必要となることもあります。  
  
## 関連規則  
 [CA1709: 識別子では、大文字と小文字が正しく区別されなければなりません](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: 識別子は、大文字と小文字の区別以外にも相違していなければなりません](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707: 識別子はアンダースコアを含むことはできません](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)  
  
 [CA1719: パラメーター名はメンバー名と同一にすることはできません](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)