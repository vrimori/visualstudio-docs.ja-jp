---
title: 'CA2205: Win32 API に相当するマネージ API を使用します'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
helpviewer_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 8e38a985db524b3d95c4f33a4eb4f31c909fd08c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205: Win32 API に相当するマネージ API を使用します
|||
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|CheckId|CA2205|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 プラットフォーム呼び出しメソッドが定義されているし、に、同等の機能を持つメソッドが存在する、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]クラス ライブラリです。

## <a name="rule-description"></a>規則の説明
 プラットフォーム呼び出しメソッド アンマネージ DLL 関数の呼び出しに使用され、定義を使用して、<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>属性、または`Declare`Visual Basic のキーワードです。 正しく定義されているプラットフォーム呼び出しメソッド、パラメーターと戻り値のデータ型と呼び出し規約、および文字などの正しくないフィールド仕様のマッピングの問題のある不適切な名前の関数などの問題があるため実行時に例外が生じることが設定します。 利用できる場合、通常は簡単なミスも少なくを定義およびアンマネージ メソッドを直接呼び出すよりも同等のマネージ メソッドを呼び出します。 プラットフォーム呼び出しメソッド対処する必要がある追加のセキュリティの問題につながることができますも。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、同等のマネージへの呼び出しでアンマネージ関数の呼び出しを置き換えます。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 推奨される置換メソッドが必要な機能を提供しない場合は、この規則による警告を抑制します。

## <a name="example"></a>例
 プラットフォームが次の例では、規則に違反するメソッドの定義を呼び出します。 また、プラットフォームへの呼び出しがメソッドを呼び出すし、同等のマネージ メソッドが表示されます。

 [!code-csharp[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/CSharp/ca2205-use-managed-equivalents-of-win32-api_1.cs)]
 [!code-vb[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/VisualBasic/ca2205-use-managed-equivalents-of-win32-api_1.vb)]

## <a name="related-rules"></a>関連規則
 [Ca 1404: P/invoke の直後に GetLastError を呼び出します](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)

 [CA1060: 移動 P/invoke を NativeMethods クラス](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [1400: P/invoke エントリ ポイントが存在する必要があります。](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [Ca 1401: P/invoke になりません](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [Ca 2101: P/invoke 文字列引数に対してマーシャ リングを指定します。](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)