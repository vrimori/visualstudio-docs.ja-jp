---
title: "CA1300: MessageBoxOptions を指定 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SpecifyMessageBoxOptions
- CA1300
helpviewer_keywords:
- SpecifyMessageBoxOptions
- CA1300
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e4ce736aa64cba9d66d770f3c4297c1685d690f6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300: MessageBoxOption を指定します
|||  
|-|-|  
|TypeName|SpecifyMessageBoxOptions|  
|CheckId|CA1300|  
|カテゴリ|Microsoft.Globalization|  
|互換性に影響する変更点|なし|  
  
## <a name="cause"></a>原因  
 メソッドのオーバー ロードを呼び出して、<xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName>を受け取らないメソッド、<xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName>引数。  
  
## <a name="rule-description"></a>規則の説明  
 右から左への読み取り順序を使用するカルチャで正しくメッセージ ボックスを表示する、<xref:System.Windows.Forms.MessageBoxOptions>と<xref:System.Windows.Forms.MessageBoxOptions>のメンバー、<xref:System.Windows.Forms.MessageBoxOptions>に列挙体を渡す必要があります、<xref:System.Windows.Forms.MessageBox.Show%2A>メソッドです。 確認、<xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName>右から左への読み取り順序を使用するかどうかを決定するコンテナー コントロールのプロパティです。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、オーバー ロードを呼び出し、<xref:System.Windows.Forms.MessageBox.Show%2A>を受け取るメソッド、<xref:System.Windows.Forms.MessageBoxOptions>引数。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 コード ライブラリを右から左への読み取り順序を使用するカルチャのローカライズしないときにこの規則による警告を抑制しても安全です。  
  
## <a name="example"></a>例  
 次の例では、カルチャの読み取り順序に対応するオプションがメッセージ ボックスを表示する方法を示します。 例をビルドするには、示されていませんが、リソース ファイルが必要です。 リソース ファイルなしの例をビルドし、右から左への機能をテストする例のコメントに従います。  
  
 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/VisualBasic/ca1300-specify-messageboxoptions_1.vb)]
 [!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/CSharp/ca1300-specify-messageboxoptions_1.cs)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Resources.ResourceManager?displayProperty=fullName>   
 [デスクトップ アプリケーションのリソース](/dotnet/framework/resources/index)