---
title: 'Ca 1302: ロケール特有の文字列をハードコードにしません |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
helpviewer_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 23f2b807d66662691afaa4805a50b34255a39bdb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49842418"
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302: ロケール特有の文字列をハードコードしません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotHardcodeLocaleSpecificStrings|
|CheckId|CA1302|
|カテゴリ|Microsoft.Globalization|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 メソッドは、特定のシステム フォルダーのパスの部分を表す文字列リテラルを使用します。

## <a name="rule-description"></a>規則の説明
 <xref:System.Environment.SpecialFolder?displayProperty=fullName>列挙が特殊なシステム フォルダーを参照するメンバーが含まれます。 これらのフォルダーの場所は、さまざまなオペレーティング システムで異なる値を持つことができます、ユーザーは、いくつかの場所を変更できるし、位置がローカライズされます。 特別なフォルダーの例の"C:\WINDOWS\system32"は、[システム] フォルダーは、[!INCLUDE[winxp](../includes/winxp-md.md)]が上には、"C:\WINNT\system32"[!INCLUDE[win2kfamily](../includes/win2kfamily-md.md)]します。 <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName>メソッドが関連付けられている場所を返します、<xref:System.Environment.SpecialFolder>列挙体。 によって返される場所<xref:System.Environment.GetFolderPath%2A>はローカライズされ、現在実行中のコンピューターに適切な。

 このルールを使用して取得されるフォルダーのパスをトークン化、<xref:System.Environment.GetFolderPath%2A>メソッドの別のディレクトリのレベルにします。 各文字列リテラルは、トークンと比較されます。 一致が見つかった場合、メソッドがトークンに関連付けられているシステムの場所を表す文字列を構築するいると見なされます。 移植性と、使用、<xref:System.Environment.GetFolderPath%2A>文字列リテラルを使用する代わりに特殊なシステム フォルダーの場所を取得するメソッド。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するを使用して場所を取得、<xref:System.Environment.GetFolderPath%2A>メソッド。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 関連付けられているシステムの場所のいずれかを参照する文字列リテラルを使用しない場合は、この規則による警告を抑制するのには安全では、<xref:System.Environment.SpecialFolder>列挙体。

## <a name="example"></a>例
 次の例では、この規則から 3 つの警告を生成します。 一般的なアプリケーション データ フォルダーのパスを構築します。 次に、例を使用して、パスを取得、<xref:System.Environment.GetFolderPath%2A>メソッド。

 [!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/cs/FxCop.Globalization.HardcodedLocaleStrings.cs#1)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/vb/FxCop.Globalization.HardcodedLocaleStrings.vb#1)]

## <a name="related-rules"></a>関連規則
 [CA1303: ローカライズされたパラメーターとしてリテラルを渡さないでください](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)



