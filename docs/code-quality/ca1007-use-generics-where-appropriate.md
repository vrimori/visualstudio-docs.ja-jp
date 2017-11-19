---
title: "Ca 1007: 適切な場所にジェネリックを使用します |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1007
- UseGenericsWhereAppropriate
helpviewer_keywords:
- CA1007
- UseGenericsWhereAppropriate
ms.assetid: eab780ea-3b1f-4d32-b15a-5d48da2df46b
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 47ee7caafdadd94f7d4ffaaca68a412e406c7c87
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="ca1007-use-generics-where-appropriate"></a>CA1007: 適切な場所にジェネリックを使用します
|||  
|-|-|  
|TypeName|UseGenericsWhereAppropriate|  
|CheckId|CA1007|  
|カテゴリ|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 外部から参照できるメソッドには、型の参照パラメーターが含まれています。 <xref:System.Object?displayProperty=fullName>、とを含むアセンブリのターゲット[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]です。  
  
## <a name="rule-description"></a>規則の説明  
 参照パラメーターはパラメーターを使用して変更を`ref`(`ByRef`で[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) キーワード。 参照パラメーターに指定された引数の型は参照パラメーターの型と正確に一致する必要があります。 参照パラメーターの型から派生した型を使用して、型必要があります最初キャストし、参照パラメーターの型の変数に割り当てられています。 ジェネリック メソッドを使用するには、適用される制限が、最初の型参照パラメーターの型にキャストせず、メソッドに渡される、すべての型が使用できます。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、メソッドを汎用的なものし、交換、<xref:System.Object>型パラメーターを使用してパラメーター。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## <a name="example"></a>例  
 次の例では、非ジェネリックとジェネリック メソッドの両方として実装されている汎用スワップ ルーチンを示します。 非ジェネリックのメソッドと比較して、ジェネリック メソッドを使用して、文字列をスワップする効率的な方法に注意してください。  
  
 [!code-vb[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/VisualBasic/ca1007-use-generics-where-appropriate_1.vb)]
 [!code-csharp[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/CSharp/ca1007-use-generics-where-appropriate_1.cs)]  
  
## <a name="related-rules"></a>関連規則  
 [CA1005: ジェネリック型でパラメーターを使用しすぎないでください](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: コレクションは、ジェネリック インターフェイスを実装しなければなりません](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: ジェネリック型の静的メンバーを宣言しません](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: ジェネリック リストを公開しません](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006: ジェネリック型をメンバー シグネチャ内で入れ子にしません](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: ジェネリック メソッドは型パラメーターを指定しなければなりません](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: 汎用イベント ハンドラーのインスタンスを使用します](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
## <a name="see-also"></a>関連項目  
 [ジェネリック](/dotnet/csharp/programming-guide/generics/index)