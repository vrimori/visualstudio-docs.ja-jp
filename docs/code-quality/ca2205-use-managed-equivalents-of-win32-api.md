---
title: CA2205:Win32 API に相当するマネージド API を使用します
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 2918750c2128b9f0eab53397b4aaf4c0cc9b6702
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55019763"
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205:Win32 API に相当するマネージド API を使用します

|||
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|CheckId|CA2205|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因

プラットフォーム呼び出しメソッドが定義されているし、.NET Framework クラス ライブラリで同等の機能を持つメソッドが存在します。

## <a name="rule-description"></a>規則の説明

プラットフォーム呼び出しメソッドをアンマネージ DLL 関数の呼び出しに使用されを使用して定義、<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>属性、または`Declare`Visual basic のキーワード。 定義済みの正しくない、プラットフォーム呼び出しメソッド パラメーターと戻り値のデータ型、および呼び出し規約、および文字など、不適切なフィールドの仕様のマッピングの問題のある不適切な名前の関数などの問題のためのランタイム例外につながる設定します。 場合より簡単かつエラーに定義および非管理対象のメソッドを直接呼び出すよりも同等のマネージ メソッドを呼び出すしやすくなります。 プラットフォーム呼び出しメソッド対処する必要がある追加のセキュリティ問題につながることもできます。

## <a name="how-to-fix-violations"></a>違反の修正方法

このルールの違反を修正するには、アンマネージ関数の呼び出しを同等のマネージの呼び出しで置き換えます。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

推奨される代替メソッドが必要な機能を提供しない場合は、この規則による警告を抑制します。

## <a name="example"></a>例

プラットフォームは、次の例は、規則に違反するメソッドの定義を呼び出します。 さらに、プラットフォーム呼び出しメソッドの呼び出しし、同等のマネージ メソッドが表示されます。

[!code-csharp[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/CSharp/ca2205-use-managed-equivalents-of-win32-api_1.cs)]
[!code-vb[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/VisualBasic/ca2205-use-managed-equivalents-of-win32-api_1.vb)]

## <a name="related-rules"></a>関連するルール

- [CA 1404:P/invoke の直後に GetLastError を呼び出します](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)
- [CA1060:P/invoke を NativeMethods クラスに移動します。](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)
- [CA1400:P/invoke エントリ ポイントが存在する必要があります。](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)
- [CA1401:P/invoke を表示することはできません。](../code-quality/ca1401-p-invokes-should-not-be-visible.md)
- [CA 2101:P/invoke 文字列引数に対してマーシャ リングを指定します。](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)