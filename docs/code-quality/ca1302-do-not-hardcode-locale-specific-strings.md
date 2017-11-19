---
title: "Ca 1302: ロケール特有の文字列をハードコードにしません |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
helpviewer_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9a6fc1bac1b13d432f395842c7de4ce6250dd708
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302: ロケール特有の文字列をハードコードしません
|||  
|-|-|  
|TypeName|DoNotHardcodeLocaleSpecificStrings|  
|CheckId|CA1302|  
|カテゴリ|Microsoft.Globalization|  
|互換性に影響する変更点|なし|  
  
## <a name="cause"></a>原因  
 メソッドは、特定のシステム フォルダーのパスの部分を表す文字列リテラルを使用します。  
  
## <a name="rule-description"></a>規則の説明  
 <xref:System.Environment.SpecialFolder?displayProperty=fullName>列挙には、特殊なシステム フォルダーを参照するメンバーが含まれています。 これらのフォルダーの場所が異なるオペレーティング システム上の異なる値を持つことができます、ユーザーによって変更する、場所のおよび位置がローカライズされます。 特別なフォルダーの例では、"C:\WINDOWS\system32"は、[システム] フォルダーが上[!INCLUDE[winxp](../code-quality/includes/winxp_md.md)]が上には、"C:\WINNT\system32"[!INCLUDE[win2kfamily](../code-quality/includes/win2kfamily_md.md)]です。 <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName>メソッドが関連付けられている場所を返します、<xref:System.Environment.SpecialFolder>列挙します。 によって返される場所<xref:System.Environment.GetFolderPath%2A>はローカライズされ、現在実行中のコンピューターに適切な。  
  
 このルールを使用して取得されるフォルダーのパスをトークン化、<xref:System.Environment.GetFolderPath%2A>個別のディレクトリのレベルにメソッドです。 各文字列リテラルは、トークンと比較されます。 一致が見つかった場合、メソッドがトークンに関連付けられているシステムの場所を表す文字列を構築するいると見なされます。 移植性と、使用、<xref:System.Environment.GetFolderPath%2A>文字列リテラルを使用する代わりに特殊なシステム フォルダーの場所を取得します。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するを使用して場所を取得、<xref:System.Environment.GetFolderPath%2A>メソッドです。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 関連付けられているシステムの場所のいずれかを参照する文字列リテラルを使用しない場合は、この規則による警告を抑制するのには安全では、<xref:System.Environment.SpecialFolder>列挙します。  
  
## <a name="example"></a>例  
 次の例では、この規則から 3 つの警告を生成する一般的なアプリケーション データ フォルダーのパスを構築します。 次に、例では、パスを取得しますを使用して、<xref:System.Environment.GetFolderPath%2A>メソッドです。  
  
 [!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/CSharp/ca1302-do-not-hardcode-locale-specific-strings_1.cs)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/VisualBasic/ca1302-do-not-hardcode-locale-specific-strings_1.vb)]  
  
## <a name="related-rules"></a>関連規則  
 [CA1303: ローカライズされたパラメーターとしてリテラルを渡さないでください](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)