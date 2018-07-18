---
title: 'CA1300: MessageBoxOption を指定します'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyMessageBoxOptions
- CA1300
helpviewer_keywords:
- SpecifyMessageBoxOptions
- CA1300
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 815fe7b7f839adeb3204e33bb532b70909d92b53
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056388"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300: MessageBoxOption を指定します

|||
|-|-|
|TypeName|SpecifyMessageBoxOptions|
|CheckId|CA1300|
|カテゴリ|Microsoft.Globalization|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因

メソッドのオーバー ロードを呼び出し、<xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName>を受け取らないメソッドを<xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName>引数。

## <a name="rule-description"></a>規則の説明

右から左への読み取り順序を使用するカルチャを正しくメッセージ ボックスを表示する、 [MessageBoxOptions.RightAlign](<xref:System.Windows.Forms.MessageBoxOptions.RightAlign>)と[MessageBoxOptions.RtlReading](<xref:System.Windows.Forms.MessageBoxOptions.RtlReading>)フィールドを<xref:System.Windows.Forms.MessageBox.Show%2A>メソッド。 確認、<xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName>右から左への読み取り順序を使用するかどうかを判断する格納しているコントロールのプロパティ。

## <a name="how-to-fix-violations"></a>違反の修正方法

この規則違反を修正するには、オーバー ロードを呼び出して、<xref:System.Windows.Forms.MessageBox.Show%2A>を受け取るメソッドを<xref:System.Windows.Forms.MessageBoxOptions>引数。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

コード ライブラリが右から左への読み取り順序を使用するカルチャのローカライズされていない、ときに、この規則による警告を抑制しても安全になります。

## <a name="example"></a>例

次の例では、カルチャの読み取り順序の適切なオプションを含むメッセージ ボックスを表示する方法を示します。 例をビルドするには示していませんが、リソース ファイルが必要です。 リソース ファイルなしの例をビルドして、右から左の機能をテストする例ではコメントに従ってください。

[!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/VisualBasic/ca1300-specify-messageboxoptions_1.vb)]
[!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/CSharp/ca1300-specify-messageboxoptions_1.cs)]

## <a name="see-also"></a>関連項目

- <xref:System.Resources.ResourceManager?displayProperty=fullName>
- [デスクトップ アプリケーションのリソース (.NET Framework)](/dotnet/framework/resources/index)