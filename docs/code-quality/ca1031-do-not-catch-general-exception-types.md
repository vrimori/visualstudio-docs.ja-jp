---
title: 'CA1031: 一般的な例外の種類はキャッチしません'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
helpviewer_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fb251798d4e1908c31d19356e711215baa52929d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: 一般的な例外の種類はキャッチしません
|||
|-|-|
|TypeName|DoNotCatchGeneralExceptionTypes|
|CheckId|CA1031|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 など、一般的な例外<xref:System.Exception?displayProperty=fullName>または<xref:System.SystemException?displayProperty=fullName>でキャッチされましたが、`catch`ステートメント、またはなどの一般的な catch 句`catch()`を使用します。

## <a name="rule-description"></a>規則の説明
 汎用的な例外はキャッチしないでください。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、例外をキャッチする具体的なまたは最後のステートメントで、汎用的な例外を再スロー、`catch`ブロックします。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。 一般的な例外の種類をキャッチして、ライブラリ ユーザーから、実行時の問題を隠すことができる、デバッグが困難なです。

> [!NOTE]
>  以降で、 [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)]、共通言語ランタイム (CLR) は、オペレーティング システムとのアクセス違反などのマネージ コードで発生する破損状態例外を不要になった配信[!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]、マネージ コードで処理されることです。 アプリケーションをコンパイルする場合、[!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)]以降のバージョン管理と破損状態例外の処理、割り当てることができます、<xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>属性を破損状態例外を処理するメソッドをします。

## <a name="example"></a>例
 次の例は、この規則に違反する型と正しく実装する型、`catch`ブロックします。

 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CPP/ca1031-do-not-catch-general-exception-types_1.cpp)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/VisualBasic/ca1031-do-not-catch-general-exception-types_1.vb)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CSharp/ca1031-do-not-catch-general-exception-types_1.cs)]

## <a name="related-rules"></a>関連規則
 [CA2200: スタック詳細を保持するために再度スローします](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)