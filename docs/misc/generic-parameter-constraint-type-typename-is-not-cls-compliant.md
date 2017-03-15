---
title: "ジェネリック パラメーターの制約型 &lt;typename&gt; は CLS に準拠していません | Microsoft Docs"
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
  - "bc40040"
  - "vbc40040"
helpviewer_keywords: 
  - "BC40040"
ms.assetid: c640dd59-56a9-43ed-b199-32a60f7b9b06
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ジェネリック パラメーターの制約型 &lt;typename&gt; は CLS に準拠していません
ジェネリック型が `<CLSCompliant(True)>` としてマークされていますが、1 つの型パラメーターに対する制約で指定している型が `<CLSCompliant(False)>` としてマークされているか、マークされていないか、非準拠の型であるため修飾されていません。  
  
 型を[言語への非依存性、および言語非依存コンポーネント](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\) 準拠にするには、CLS 準拠の型のみを使用する必要があります。 このことは、ジェネリック型の型パラメーターに対する制約にも当てはまります。  
  
 次の [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] データ型は CLS に準拠していません。  
  
-   [SByte Data Type](/dotnet/visual-basic/language-reference/data-types/sbyte-data-type)  
  
-   [UInteger Data Type](/dotnet/visual-basic/language-reference/data-types/uinteger-data-type)  
  
-   [ULong Data Type](/dotnet/visual-basic/language-reference/data-types/ulong-data-type)  
  
-   [UShort Data Type](/dotnet/visual-basic/language-reference/data-types/ushort-data-type)  
  
 プログラミング要素に <xref:System.CLSCompliantAttribute> 属性を適用するときは、属性の `isCompliant` パラメーターを `True` または `False` のどちらかに設定して、準拠または非準拠を示します。 このパラメーターには既定値がありませんので、値を指定する必要があります。  
  
 要素に <xref:System.CLSCompliantAttribute> を適用しないと、その要素は非準拠と見なされます。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」を参照してください。  
  
 **エラー ID:** BC40040  
  
### このエラーを解決するには  
  
-   ジェネリック型が、この特定の型で制限された型パラメーターを使用する必要がある場合は、<xref:System.CLSCompliantAttribute> を削除します。 この型は CLS 準拠になりません。  
  
-   ジェネリック型を CLS 準拠にする必要がある場合は、この制約の型を、最も近い CLS 準拠型に変更します。 たとえば、2,147,483,647 を超える値の範囲が不要な場合は、`UInteger` の代わりに `Integer` を使用できます。 拡張範囲が必要な場合は、`UInteger` の代わりに `Long` を使用できます。  
  
## 参照  
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [\<PAVE OVER\> CLS 準拠コードの記述](http://msdn.microsoft.com/ja-jp/4c705105-69a2-4e5e-b24e-0633bc32c7f3)