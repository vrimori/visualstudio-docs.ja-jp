---
title: '1402: COM 参照可能インターフェイスでのオーバー ロードを避けてください |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
helpviewer_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
ms.assetid: 2724c1f9-d5d3-4704-b124-21c4d398e5df
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ece9a444ac308003c56da1bd4f2ecf4433e2b4a9
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589197"
---
# <a name="ca1402-avoid-overloads-in-com-visible-interfaces"></a>CA1402: COM 参照可能インターフェイスでのオーバーロードを避けてください
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ca 1402: COM 参照可能インターフェイスでオーバー ロードを避けて](https://docs.microsoft.com/visualstudio/code-quality/ca1402-avoid-overloads-in-com-visible-interfaces)します。

|||
|-|-|
|TypeName|AvoidOverloadsInComVisibleInterfaces|
|CheckId|CA1402|
|カテゴリ|Microsoft.Interoperability|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 オーバー ロードされたメソッドのコンポーネント オブジェクト モデル (COM) 参照できるインターフェイスを宣言します。

## <a name="rule-description"></a>規則の説明
 オーバーロードされたメソッドが COM クライアントに公開されると、最初のメソッド オーバーロードだけが名前を保持します。 後続のオーバー ロードが名前にアンダー スコア文字 '_' とオーバー ロードの宣言の順序に対応する整数を追加して一意に変更されます。 たとえば、次の方法を検討してください。

```
void SomeMethod(int valueOne);
void SomeMethod(int valueOne, int valueTwo, int valueThree);
void SomeMethod(int valueOne, int valueTwo);
```

 これらのメソッドは、次のように COM クライアントに公開されます。

```
void SomeMethod(int valueOne);
void SomeMethod_2(int valueOne, int valueTwo, int valueThree);
void SomeMethod_3(int valueOne, int valueTwo);
```

 Visual Basic 6 COM クライアントは、名前にアンダー スコアを使用して、インターフェイス メソッドを実装することはできません。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、名前が一意になるため、オーバー ロードされたメソッドの名前を変更します。 またへのアクセシビリティを変更することで、インターフェイスが COM に非表示こと`internal`(`Friend`で[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) または適用することで、<xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>属性に設定`false`します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、インターフェイス、規則に違反して、規則に適合するインターフェイスを示します。

 [!code-csharp[FxCop.Interoperability.OverloadsInterface#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.OverloadsInterface/cs/FxCop.Interoperability.OverloadsInterface.cs#1)]
 [!code-vb[FxCop.Interoperability.OverloadsInterface#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.OverloadsInterface/vb/FxCop.Interoperability.OverloadsInterface.vb#1)]

## <a name="related-rules"></a>関連規則
 [CA1413: Com 参照可能な値型ではパブリックでないフィールドを使用しません](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407: Com 参照可能な型で静的メンバーを使用しません](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: アセンブリに ComVisibleAttribute を設定します](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>関連項目
 [アンマネージ コードと相互運用](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [Long データ型](http://msdn.microsoft.com/library/b4770c34-1804-4f8c-b512-c10b0893e516)



