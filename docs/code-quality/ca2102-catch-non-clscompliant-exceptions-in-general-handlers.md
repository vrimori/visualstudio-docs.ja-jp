---
title: 'CA2102: 汎用ハンドラーの CLSCompliant でない例外をキャッチします'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2102
- CatchNonClsCompliantExceptionsInGeneralHandlers
helpviewer_keywords:
- CA2102
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f32e6fa3d1dfc3c8ee0f116a6e06de49c90ea256
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31916435"
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102: 汎用ハンドラーの CLSCompliant でない例外をキャッチします
|||
|-|-|
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|
|CheckId|CA2102|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 マークされていないアセンブリ内のメンバー、<xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute>またはマークされて`RuntimeCompatibility(WrapNonExceptionThrows = false)`を処理する catch ブロックを含む<xref:System.Exception?displayProperty=fullName>直後に汎用 catch ブロックが含まれていないとします。 この規則は無視されます[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]アセンブリ。

## <a name="rule-description"></a>規則の説明
 処理する catch ブロック<xref:System.Exception>共通言語仕様 (CLS) 準拠のすべての例外をキャッチします。 ただし、非 CLS 準拠の例外はキャッチしません。 非 CLS 準拠でネイティブ コードとは、Microsoft によって生成されたマネージ コードから、準拠しない例外をスローできる language (MSIL) の中間アセンブラーです。 注意して、c# と[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]コンパイラ許可しない非 CLS 準拠の例外をスローし、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]非 CLS 準拠の例外をキャッチしません。 すべての例外を処理する catch ブロックの目的がある場合は、次の汎用 catch ブロックの構文を使用します。

-   C#: `catch {}`

-   C++:`catch(...) {}`または `catch(Object^) {}`

 未処理の非 CLS 準拠の例外は、catch ブロックで以前に許可されたアクセス許可を削除するとセキュリティの問題になります。 非 CLS に準拠しない例外がキャッチされないので、CLS に準拠している例外をスローする悪意のあるメソッドの管理者特権を持つ実行可能性があります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 目的は、すべてをキャッチする場合に、この規則違反を修正する例外、または汎用 catch ブロックを追加またはアセンブリをマーク`RuntimeCompatibility(WrapNonExceptionThrows = true)`です。 場合は、catch ブロックでのアクセス許可が削除されると、重複する一般的な機能は、catch ブロック。 そうでないすべての例外処理を目的とした場合を処理する catch ブロックを置き換える<xref:System.Exception>特定の例外の種類に対応する catch ブロック。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 非 CLS 準拠の例外が生成するすべてのステートメントが try ブロックに含まれていない場合は、この規則による警告を抑制するのには安全です。 ネイティブまたはマネージ コード時に非 CLS 準拠で例外をスローする可能性があります、try ブロック内のすべてのコード パスで実行できるすべてのコードの知識が必要です。 共通言語ランタイムによって、CLS に準拠しない例外がスローされないことに注意してください。

## <a name="example"></a>例
 次の例では、CLS 非準拠の例外をスローする MSIL クラスを示します。

```
.assembly ThrowNonClsCompliantException {}
.class public auto ansi beforefieldinit ThrowsExceptions
{
   .method public hidebysig static void
         ThrowNonClsException() cil managed
   {
      .maxstack  1
      IL_0000:  newobj     instance void [mscorlib]System.Object::.ctor()
      IL_0005:  throw
   }
}
```

## <a name="example"></a>例
 次の例では、ルールを満たす汎用 catch ブロックが含まれているメソッドを示します。

 [!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../code-quality/codesnippet/CSharp/ca2102-catch-non-clscompliant-exceptions-in-general-handlers_1.cs)]

 前の例を次のようにコンパイルします。

```
ilasm /dll ThrowNonClsCompliantException.il
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs
```

## <a name="related-rules"></a>関連規則
 [CA1031: 一般的な例外の種類はキャッチしません](../code-quality/ca1031-do-not-catch-general-exception-types.md)

## <a name="see-also"></a>関連項目
 [例外と例外処理](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling) [Ilasm.exe (IL アセンブラー)](/dotnet/framework/tools/ilasm-exe-il-assembler) [言語非依存および言語非依存コンポーネント](/dotnet/standard/language-independence-and-language-independent-components)