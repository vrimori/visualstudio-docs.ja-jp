---
title: "Ca 1003: 汎用イベント ハンドラーのインスタンスを使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cf4f11f3f8fae1130c2cc99468a40ed269c77481
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003: 汎用イベント ハンドラーのインスタンスを使用します
|||  
|-|-|  
|TypeName|UseGenericEventHandlerInstances|  
|CheckId|CA1003|  
|カテゴリ|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 型が void を返す、2 つのパラメーター (1 つはオブジェクトと、2 つ目は EventArgs に割り当て可能な型) と包含アセンブリの対象を含むシグネチャを持つデリゲートを含む[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]です。  
  
## <a name="rule-description"></a>規則の説明  
 前に[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]イベント ハンドラーにカスタム情報を渡すために、新しいデリゲートを宣言するのにはから派生したクラスを指定する必要がある、<xref:System.EventArgs?displayProperty=fullName>クラスです。 これは true ではなく[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]、導入された、<xref:System.EventHandler%601?displayProperty=fullName>委任します。 この汎用デリゲートにより、任意のクラスから派生した<xref:System.EventArgs>イベントのハンドラーと共に使用します。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、デリゲートを削除しを使用してその用途を置き換えて、<xref:System.EventHandler%601?displayProperty=fullName>を委任します。 デリゲートは、によって自動生成された場合、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]コンパイラを使用するイベントの宣言の構文を変更、<xref:System.EventHandler%601?displayProperty=fullName>を委任します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## <a name="example"></a>例  
 次の例では、規則に違反するデリゲートを示します。 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]例では、コメントは、規則に適合するように例を変更する方法を説明します。 たとえば、C# の場合、次に例を修正したコードを表示します。  
  
 [!code-vb[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/VisualBasic/ca1003-use-generic-event-handler-instances_1.vb)]
 [!code-csharp[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_1.cs)]  
  
## <a name="example"></a>例  
 次の例では、デリゲート宣言を削除、規則に適合し、その使用を置き換えますが前の例から、`ClassThatRaisesEvent`と`ClassThatHandlesEvent`メソッドを使用して、<xref:System.EventHandler%601?displayProperty=fullName>を委任します。  
  
 [!code-csharp[FxCop.Design.GenericEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_2.cs)]  
  
## <a name="related-rules"></a>関連規則  
 [CA1005: ジェネリック型でパラメーターを使用しすぎないでください](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: コレクションは、ジェネリック インターフェイスを実装しなければなりません](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: ジェネリック型の静的メンバーを宣言しません](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: ジェネリック リストを公開しません](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006: ジェネリック型をメンバー シグネチャ内で入れ子にしません](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: ジェネリック メソッドは型パラメーターを指定しなければなりません](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1007: 適切な場所にジェネリックを使用します](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## <a name="see-also"></a>関連項目  
 [ジェネリック](/dotnet/csharp/programming-guide/generics/index)