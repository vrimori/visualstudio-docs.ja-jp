---
title: CA2201:予約された例外の種類を発生させません
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- DoNotRaiseReservedExceptionTypes
- CA2201
helpviewer_keywords:
- CA2201
- DoNotRaiseReservedExceptionTypes
ms.assetid: dd14ef5c-80e6-41a5-834e-eba8e2eae75e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9b8eff3ac514e82e16327bfb873ed5fa2e9ccfba
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53911940"
---
# <a name="ca2201-do-not-raise-reserved-exception-types"></a>CA2201:予約された例外の種類を発生させません

|||
|-|-|
|TypeName|DoNotRaiseReservedExceptionTypes|
|CheckId|CA2201|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因

メソッドは、一般的すぎるか、ランタイムによって予約されている例外の種類を発生させます。

## <a name="rule-description"></a>規則の説明

次の例外の種類は、ユーザーに十分な情報を提供する汎用的です。

- <xref:System.Exception?displayProperty=fullName>

- <xref:System.ApplicationException?displayProperty=fullName>

- <xref:System.SystemException?displayProperty=fullName>

次の例外の種類は予約されており、共通言語ランタイムによってのみスローする必要があります。

- <xref:System.ExecutionEngineException?displayProperty=fullName>

- <xref:System.IndexOutOfRangeException?displayProperty=fullName>

- <xref:System.NullReferenceException?displayProperty=fullName>

- <xref:System.OutOfMemoryException?displayProperty=fullName>

**一般的な例外をスローしないでください。**

など、一般的な例外型をスローするかどうかは<xref:System.Exception>または<xref:System.SystemException>が強制的にライブラリまたはフレームワークでは、すべてをキャッチするコンシューマーを処理する方法がわからない不明な例外を含む例外。

代わりに、framework では、既に存在するより強い派生型をスローまたはのいずれかから派生した独自の型を作成する<xref:System.Exception>します。

**特定の例外をスローします。**

次の表に、パラメーターとプロパティの set アクセサーに値パラメーターを含め、パラメーターを検証する場合にスローされる例外。

|パラメーターの説明|例外|
|---------------------------|---------------|
|`null` 参照|<xref:System.ArgumentNullException?displayProperty=fullName>|
|(コレクションまたはリストのインデックス) などの値の許容範囲外|<xref:System.ArgumentOutOfRangeException?displayProperty=fullName>|
|無効な`enum`値|<xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=fullName>|
|メソッドのパラメーターの仕様を満たしていない形式が含まれています (などの書式指定文字列`ToString(String)`)|<xref:System.FormatException?displayProperty=fullName>|
|それ以外の場合が無効です。|<xref:System.ArgumentException?displayProperty=fullName>|

操作が、オブジェクトのスローの現在の状態の有効な場合 <xref:System.InvalidOperationException?displayProperty=fullName>

操作が破棄されているオブジェクトで実行されるとスローします。 <xref:System.ObjectDisposedException?displayProperty=fullName>

操作がサポートされていない場合 (このようなようにオーバーライドされた**Stream.Write**読み取り用に開く Stream で) をスロー <xref:System.NotSupportedException?displayProperty=fullName>

変換すると、オーバーフロー (明示的なキャスト演算子のオーバー ロードなど) で、ときにスローします。 <xref:System.OverflowException?displayProperty=fullName>

その他のすべての状況から派生した独自の型の作成を検討して<xref:System.Exception>をスローします。

## <a name="how-to-fix-violations"></a>違反の修正方法

この規則違反を解決するには、予約の種類のいずれかではない特定の型に、スローされた例外の種類を変更します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

この規則による警告は抑制しないでください。

## <a name="related-rules"></a>関連するルール

- [CA 1031:一般的な例外の種類はキャッチしません](../code-quality/ca1031-do-not-catch-general-exception-types.md)