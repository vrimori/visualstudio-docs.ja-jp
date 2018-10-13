---
title: 'Ca 2102: 汎用ハンドラーで非 CLSCompliant の例外をキャッチする |Microsoft Docs'
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
- CA2102
- CatchNonClsCompliantExceptionsInGeneralHandlers
helpviewer_keywords:
- CA2102
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c9b08b143df05ec365c069d4c6dbf7d9ed84813d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49244875"
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102: 汎用ハンドラーの CLSCompliant でない例外をキャッチします
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|
|CheckId|CA2102|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 マークされていないアセンブリ内のメンバー、<xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute>またはマークされている`RuntimeCompatibility(WrapNonExceptionThrows = false)`を処理する catch ブロックが含まれています<xref:System.Exception?displayProperty=fullName>直後に汎用の catch ブロックを含んでいません。 この規則は無視されます[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]アセンブリ。

## <a name="rule-description"></a>規則の説明
 処理する catch ブロック<xref:System.Exception>共通言語仕様 (CLS) 準拠のすべての例外をキャッチします。 ただし、CLS 非準拠の例外はキャッチしません。 非 CLS 準拠でネイティブ コードまたは Microsoft によって生成されたマネージ コードから、準拠しない例外をスローできます intermediate language (MSIL) アセンブラー。 注意して、c# と[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]コンパイラできないようにする CLS 非準拠の例外をスローし、 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] CLS 非準拠の例外をキャッチしません。 すべての例外を処理する catch ブロックの目的がある場合は、次の汎用の catch ブロックの構文を使用します。

-   C#: `catch {}`

-   C++:`catch(...) {}`または `catch(Object^) {}`

 Catch ブロックで以前に許可されたアクセス許可が削除されたときのセキュリティの問題を処理できない CLS 準拠の例外になります。 CLS 非準拠の例外はキャッチされないため、CLS に準拠している例外をスローする悪意のあるメソッドは、管理者特権を持つ実行でした。

## <a name="how-to-fix-violations"></a>違反の修正方法
 目的は、すべてをキャッチするときに、この規則の違反を修正する例外を置き換える汎用 catch ブロックを追加またはアセンブリをマーク`RuntimeCompatibility(WrapNonExceptionThrows = true)`します。 場合は、catch ブロックでのアクセス許可が削除されると、重複する機能は、一般的な catch ブロック。 すべての例外を処理するために意図されていない場合を処理する catch ブロックを置き換える<xref:System.Exception>で特定の例外の種類に対応する catch ブロック。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 CLS 非準拠の例外を生成するすべてのステートメントが try ブロックに含まれていない場合、この規則による警告を抑制するのには安全です。 ネイティブまたはマネージ コードは、CLS に準拠している例外をスロー可能性があります、ため、この try ブロック内部のすべてのコード パスで実行できるすべてのコードの知識が必要です。 CLS 非準拠の例外が共通言語ランタイムによってスローされるしないことに注意してください。

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
 次の例では、規則に適合する汎用の catch ブロックを含むメソッドを示します。

 [!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.CatchNonClsCompliantException/cs/FxCop.Security.CatchNonClsCompliantException.cs#1)]

 次のように、前の例をコンパイルします。

```
ilasm /dll ThrowNonClsCompliantException.il
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs
```

## <a name="related-rules"></a>関連規則
 [CA1031: 一般的な例外の種類はキャッチしません](../code-quality/ca1031-do-not-catch-general-exception-types.md)

## <a name="see-also"></a>関連項目
 [例外と例外処理](http://msdn.microsoft.com/library/0001887f-4fa2-47e2-8034-2819477e2344) [Ilasm.exe (IL アセンブラー)](http://msdn.microsoft.com/library/4ca3a4f0-4400-47ce-8936-8e219961c76f) [セキュリティ チェックをオーバーライドする](http://msdn.microsoft.com/en-us/4acdeff5-fc05-41bf-8505-7387cdbfca28) [Language Independence and Language-independent Components](http://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)



