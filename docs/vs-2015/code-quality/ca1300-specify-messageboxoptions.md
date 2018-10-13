---
title: 'Ca 1300: Messageboxoption を指定します |Microsoft Docs'
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
- SpecifyMessageBoxOptions
- CA1300
helpviewer_keywords:
- SpecifyMessageBoxOptions
- CA1300
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 157cac1ddd200799b0362529c0a434086db77781
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49288926"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300: MessageBoxOption を指定します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|SpecifyMessageBoxOptions|
|CheckId|CA1300|
|カテゴリ|Microsoft.Globalization|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 メソッドのオーバー ロードを呼び出し、<xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName>を受け取らないメソッドを<xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName>引数。

## <a name="rule-description"></a>規則の説明
 右から左への読み取り順序を使用するカルチャを正しくメッセージ ボックスを表示する、<xref:System.Windows.Forms.MessageBoxOptions>と<xref:System.Windows.Forms.MessageBoxOptions>のメンバー、<xref:System.Windows.Forms.MessageBoxOptions>に列挙体を渡す必要があります、<xref:System.Windows.Forms.MessageBox.Show%2A>メソッド。 確認、<xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName>右から左への読み取り順序を使用するかどうかを判断する格納しているコントロールのプロパティ。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、オーバー ロードを呼び出して、<xref:System.Windows.Forms.MessageBox.Show%2A>を受け取るメソッドを<xref:System.Windows.Forms.MessageBoxOptions>引数。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 コード ライブラリが右から左への読み取り順序を使用するカルチャのローカライズされていない、ときに、この規則による警告を抑制しても安全になります。

## <a name="example"></a>例
 次の例では、カルチャの読み取り順序の適切なオプションを含むメッセージ ボックスを表示する方法を示します。 例をビルドするには示していませんが、リソース ファイルが必要です。 リソース ファイルなしの例をビルドして、右から左の機能をテストする例ではコメントに従ってください。

 [!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/cs/FxCop.Globalization.SpecifyMBOptions.cs#1)]
 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/vb/FxCop.Globalization.SpecifyMBOptions.vb#1)]

## <a name="see-also"></a>関連項目
 <xref:System.Resources.ResourceManager?displayProperty=fullName> [デスクトップ アプリでのリソース](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)



