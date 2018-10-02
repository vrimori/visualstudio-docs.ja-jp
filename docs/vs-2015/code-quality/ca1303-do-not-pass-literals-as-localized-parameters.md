---
title: 'Ca 1303: パラメーターが渡されないリテラルとローカライズ |Microsoft Docs'
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
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5fcb7f9f4cd57f287ec7a2bab900a78d21f23846
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589220"
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303: ローカライズされたパラメーターとしてリテラルを渡さないでください
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ca 1303: リテラルにローカライズされたパラメーターが渡されない](https://docs.microsoft.com/visualstudio/code-quality/ca1303-do-not-pass-literals-as-localized-parameters)します。

|||
|-|-|
|TypeName|DoNotPassLiteralsAsLocalizedParameters|
|CheckId|CA1303|
|カテゴリ|Microsoft.Globalization|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 メソッドを文字列リテラルをパラメーターとして渡しコンス トラクターまたはメソッドに、[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]クラス ライブラリおよびローカライズ可能な文字列である必要があります。

 パラメーターまたはプロパティにリテラル文字列が値として渡され、1 つ以上の次の場合は true、この警告が発生します。

-   <xref:System.ComponentModel.LocalizableAttribute>パラメーターまたはプロパティの属性が設定を true にします。

-   パラメーターまたはプロパティ名には、"Text"、"Message"または「キャプション」が含まれています。

-   Console.Write"または"Console.WriteLine メソッドに渡される文字列パラメーターの名前は、"value"または「形式」のいずれかです。

## <a name="rule-description"></a>規則の説明
 ソース コードに埋め込まれている文字列リテラルは、ローカライズが困難です。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則の違反を修正するには、インスタンスを通じて取得された文字列を文字列リテラルを置き換える、<xref:System.Resources.ResourceManager>クラス。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 コード ライブラリをローカライズしない場合、または文字列が、エンドユーザーまたはコード ライブラリを使用して開発者に公開されない場合は、この規則による警告を抑制しても安全になります。

 ユーザーは、渡す必要がないあるローカライズされた文字列パラメーターまたはという名前のプロパティを名前変更して、またはこれらのアイテムを条件付きとしてマークすることによってメソッドに対してノイズを回避できます。

## <a name="example"></a>例
 次の例では、範囲外の 2 つの引数のいずれかのときに例外をスローするメソッドを示します。 最初の引数の例外のコンス トラクターに、この規則に違反するリテラル文字列が渡されます。 2 番目の引数のコンス トラクターが正しく渡されますを介して取得された文字列を<xref:System.Resources.ResourceManager>します。

 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cpp/FxCop.Globalization.DoNotPassLiterals.cpp#1)]
 [!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cs/FxCop.Globalization.DoNotPassLiterals.cs#1)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/vb/FxCop.Globalization.DoNotPassLiterals.vb#1)]

## <a name="see-also"></a>関連項目
 [デスクトップ アプリケーションのリソース](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)



