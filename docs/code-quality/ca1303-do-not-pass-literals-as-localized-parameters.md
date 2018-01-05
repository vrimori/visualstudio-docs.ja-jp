---
title: "Ca 1303: パラメーターが渡されないリテラルにローカライズされた |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 361155e9d46e4f71ddc61775f56105cedb5d18b9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303: ローカライズされたパラメーターとしてリテラルを渡さないでください
|||  
|-|-|  
|TypeName|DoNotPassLiteralsAsLocalizedParameters|  
|CheckId|CA1303|  
|カテゴリ|Microsoft.Globalization|  
|互換性に影響する変更点|中断なし|  
  
## <a name="cause"></a>原因  
 メソッドを文字列リテラルをパラメーターとして渡しコンス トラクターまたはメソッドに、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]クラス ライブラリとその文字列はローカライズ可能です。  
  
 この警告は、リテラル文字列がパラメーターまたはプロパティに値として渡され、1 つ以上の次の場合は true。  
  
-   <xref:System.ComponentModel.LocalizableAttribute>パラメーターまたはプロパティの属性が設定を true にします。  
  
-   パラメーターまたはプロパティ名には、"Text"、「メッセージ」または「キャプション」が含まれています。  
  
-   Console.Write または Console.WriteLine メソッドに渡される文字列パラメーターの名前は"value"か"format"。  
  
## <a name="rule-description"></a>規則の説明  
 ソース コードに埋め込まれている文字列リテラルは、ローカライズするが困難です。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、インスタンスを使用して取得文字列では、リテラル文字列を置き換えます、<xref:System.Resources.ResourceManager>クラスです。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 コード ライブラリをローカライズしない、または文字列が、エンドユーザーまたはコード ライブラリを使用する開発者に公開されていない場合は、この規則による警告を抑制しても安全です。  
  
 ユーザーは、メソッドを渡すことはできませんローカライズされた文字列パラメーターまたは名前付き、プロパティを変更するか、これらのアイテムを条件付きとしてマークすることによっているに対してノイズを除去できます。  
  
## <a name="example"></a>例  
 次の例では、2 つの引数のいずれかが範囲外と例外をスローするメソッドを示します。 最初の引数では、例外のコンス トラクターは、この規則に違反するリテラル文字列で渡されます。 2 番目の引数のコンス トラクターは正常に渡されますを介して取得された文字列、<xref:System.Resources.ResourceManager>です。  
  
 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CPP/ca1303-do-not-pass-literals-as-localized-parameters_1.cpp)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/VisualBasic/ca1303-do-not-pass-literals-as-localized-parameters_1.vb)]
 [!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CSharp/ca1303-do-not-pass-literals-as-localized-parameters_1.cs)]  
  
## <a name="see-also"></a>参照  
 [デスクトップ アプリケーションのリソース](/dotnet/framework/resources/index)