---
title: CA1031:一般的な例外の種類はキャッチしません
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 844f6686205f7aaa6c1b8b8c198eb4240d6d1fab
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53878300"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031:一般的な例外の種類はキャッチしません

|||
|-|-|
|TypeName|DoNotCatchGeneralExceptionTypes|
|CheckId|CA1031|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 などの一般的な例外<xref:System.Exception?displayProperty=fullName>または<xref:System.SystemException?displayProperty=fullName>でキャッチされます、`catch`ステートメント、またはなどの一般的な catch 句`catch()`使用されます。

## <a name="rule-description"></a>規則の説明
 汎用的な例外はキャッチしないでください。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するより具体的な例外をキャッチまたは最後のステートメントとして一般的な例外を再スロー、`catch`ブロックします。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告は抑制しないでください。 一般的な例外の種類をキャッチして、ライブラリ ユーザーから、実行時の問題を非表示にすることができます、指定するとデバッグはより難しくなります。

> [!NOTE]
> 以降では、 [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)]、共通言語ランタイム (CLR) は、オペレーティング システムとでアクセス違反などのマネージ コードで発生する破損状態例外を提供できなく[!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]、マネージ コードで処理されます。 アプリケーションをコンパイルする場合、[!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)]以降のバージョンの管理と適用できる破損状態例外の処理、<xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>属性を破損状態例外を処理するメソッド。

## <a name="example"></a>例
 次の例は、この規則に違反する型と正しく実装する型、`catch`ブロックします。

 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CPP/ca1031-do-not-catch-general-exception-types_1.cpp)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/VisualBasic/ca1031-do-not-catch-general-exception-types_1.vb)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CSharp/ca1031-do-not-catch-general-exception-types_1.cs)]

## <a name="related-rules"></a>関連するルール
 [CA 2200:スタックの詳細を保持するために再スローします。](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)